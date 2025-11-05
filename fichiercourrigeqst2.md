# Créer la vue + template pour about/
# 2.1 — Créer la vue

Édite (ou crée) le fichier medico/views.py et ajoute la vue suivante :

# medico/views.py
from django.shortcuts import render

def about(request):
    """
    Page de présentation de l'application (Question 2).
    """
    context = {
        'app_name': "Gestion de consultations médicales",
        'author': "Nom du groupe / membres",
        'description': "Application destinée à un médecin pour gérer consultations et ordonnances."
    }
    return render(request, 'medico/about.html', context)

# 2.2 — Créer le template

Crée le dossier medico/templates/medico/ (respecte bien la casse) puis crée about.html dedans :

Chemin : medico/templates/medico/about.html

Contenu proposé :

<!-- medico/templates/medico/about.html -->
<!doctype html>
<html lang="fr">
  <head>
    <meta charset="utf-8">
    <title>About — Gestion Consultations</title>
  </head>
  <body>
    <h1>{{ app_name }}</h1>
    <p><strong>Auteurs :</strong> Nom1, Nom2, ...</p>
    <h2>À propos de l'application</h2>
    <p>{{ description }}</p>

    <h3>Contact</h3>
    <p>email1@univ-orleans.fr — email2@univ-orleans.fr</p>
  </body>
</html>


Remplace les noms et emails par ceux de ton groupe dans la version finale.

# 2.3 — Ajouter des URLs pour l'app medico

Crée (si pas déjà) medico/urls.py et ajoute :

# medico/urls.py
from django.urls import path
from . import views

app_name = 'medico'

urlpatterns = [
    path('about/', views.about, name='about'),
]

2.4 — Lier les URLs de l'application au projet

Ouvre cc/urls.py (à la racine du projet cc) et modifie pour inclure les URLs de l'app :

# cc/urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('medico.urls')),  # inclut about/ etc.
]