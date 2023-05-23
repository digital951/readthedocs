The following example shows how you could create an Nginx pod in Kubernetes that uses a secret to store an SSL certificate.

Firstly, let's assume that you've already created a Secret resource that contains your SSL certificate and key. The secret might be created as follows:

.. code-block:: bash

   kubectl create secret tls nginxsecret --key /path/to/tls.key --cert /path/to/tls.crt

Here ``nginxsecret`` is the name of the secret, ``tls.key`` is the private key file, and ``tls.crt`` is the certificate file.

Now, you can create the Nginx pod that uses this secret:

.. code-block:: yaml

   apiVersion: v1
   kind: Pod
   metadata:
     name: nginx
     labels:
       app: nginx
   spec:
     containers:
     - name: nginx
       image: nginx:1.19.2
       ports:
       - containerPort: 80
       - containerPort: 443
       volumeMounts:
       - name: nginx-certs
         mountPath: /etc/nginx/ssl
       - name: nginx-config-volume
         mountPath: /etc/nginx/nginx.conf
         subPath: nginx.conf
     volumes:
     - name: nginx-certs
       secret:
         secretName: nginxsecret
     - name: nginx-config-volume
       configMap:
         name: nginx-conf

In this configuration, the SSL certificate and key are mounted into the ``/etc/nginx/ssl`` directory of the Nginx container.

You'll also need to configure Nginx to use the SSL certificate by creating a ``ConfigMap`` that contains the Nginx configuration file:

.. code-block:: bash

   kubectl create configmap nginx-conf --from-file=nginx.conf=/path/to/nginx.conf

The ``nginx.conf`` file should include a section for serving over HTTPS, something like this:

.. code-block:: nginx

   server {
       listen 443 ssl;
   
       ssl_certificate /etc/nginx/ssl/tls.crt;
       ssl_certificate_key /etc/nginx/ssl/tls.key;
   
       location / {
           root /usr/share/nginx/html;
           index index.html;
       }
   }

In this configuration, Nginx serves content over HTTPS, using the certificate and key provided in the secret.
