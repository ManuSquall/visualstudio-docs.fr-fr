
1. Sur l’ordinateur où vous ouvrir le projet ASP.NET dans Visual Studio, cliquez sur le projet dans l’Explorateur de solutions, puis choisissez **publier**.

1. Si vous avez déjà configuré des profils de publication, le **publier** volet s’affiche. Cliquez sur **créer nouveau profil**.

1. Dans le **choisir une cible de publication** boîte de dialogue, cliquez sur **importer un profil**.

    ![Choisissez publier](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Accédez à l’emplacement du fichier de paramètres de publication que vous avez créé dans la section précédente.

1. Dans le **importation publier un fichier de paramètres** boîte de dialogue, accédez à et sélectionnez le profil que vous avez créé dans la section précédente, puis cliquez sur **ouvrir**.

    Visual Studio lance le processus de déploiement, et la fenêtre Sortie affiche la progression et les résultats.

    Si vous obtenez un déploiement de toutes les erreurs, cliquez sur **paramètres** pour modifier les paramètres. Modifier les paramètres et cliquez sur **Validate** pour tester les nouveaux paramètres. Si le nom d’hôte est introuvable, essayez de l’adresse IP au lieu du nom d’hôte dans le **Server** et **URL de Destination** champs.

    ![Modifier les paramètres dans l’outil de publication](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
