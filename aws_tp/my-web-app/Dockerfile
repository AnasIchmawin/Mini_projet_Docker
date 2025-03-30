# Utiliser une image de base Nginx
FROM nginx:alpine

# Copier le fichier index.html dans le dossier html de Nginx
COPY index.html /usr/share/nginx/html/

# Créer un dossier pour les images
RUN mkdir -p /usr/share/nginx/html/images

# Copier l'image dans le dossier images
COPY ../images/1.jpeg /usr/share/nginx/html/images/

# Exposer le port 80
EXPOSE 80

# Commande pour démarrer Nginx
CMD ["nginx", "-g", "daemon off;"]