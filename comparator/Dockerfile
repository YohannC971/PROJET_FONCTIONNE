# Utilise une image de base Python (3.10-slim)
FROM python:3.10-slim

# Installe les dépendances système nécessaires
RUN apt-get update && apt-get install -y \
    libpq-dev gcc && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Définit le répertoire de travail
WORKDIR /app


# Copie le fichier entrypoint.sh dans /usr/local/bin/start.sh
COPY entrypoint.sh /usr/local/bin/start.sh

# Rend le fichier exécutable
RUN chmod +x /usr/local/bin/start.sh

# Installer les dépendances Python (si fichier requirements.txt existant)
RUN if [ -f "requirements.txt" ]; then pip install -r requirements.txt; fi

# Expose le port 9000 pour le serveur Django
EXPOSE 9000

# Définit le script comme point d'entrée
ENTRYPOINT ["/usr/local/bin/start.sh"]


