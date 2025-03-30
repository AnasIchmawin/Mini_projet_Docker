# Utiliser nginx comme image de base
FROM nginx:alpine

# Informations sur le mainteneur
LABEL maintainer="votre_email@exemple.com"

# Copier le fichier index.html dans le répertoire de nginx
COPY index.html /usr/share/nginx/html/

# Exposer le port 80
EXPOSE 80

# Commande de démarrage (utilise le démarrage par défaut de nginx)
CMD ["nginx", "-g", "daemon off;"]