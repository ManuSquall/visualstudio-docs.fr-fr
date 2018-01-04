# <a name="create-an-ai-project-from-existing-code"></a>Créer un projet AI à partir d’un code existant

Une fois que vous avez [installé Visual Studio Tools pour AI](installation.md), il est facile de placer du code Python existant dans un projet Visual Studio. 

> [!Important]
>
> Le processus décrit ici ne déplace pas ou ne copie pas les fichiers sources d’origine. Si vous voulez travailler avec une copie, dupliquez d’abord le dossier.

1. Lancez Visual Studio et sélectionnez **Fichier > Nouveau > Projet**.

1. Dans la boîte de dialogue **Nouveau projet**, recherchez « **AI Tools** », sélectionnez le modèle « **À partir de code Python existant** », spécifiez un nom et un emplacement pour le projet, puis sélectionnez **OK**.

    ![Nouveau projet à partir du code existant, étape 1](media\create-project-existing\new-ai-project.png)

1. Dans l’Assistant qui apparaît, définissez le chemin de votre code existant, un filtre pour les types de fichiers et les chemins de recherche nécessaires à votre projet, puis sélectionnez **OK**. Si vous ne savez pas ce que sont les chemins de recherche, laissez ce champ vide.


![Nouveau projet à partir du code existant, étape 2](media\create-project-existing\azurebatch-newproject.png)

> Si votre code existant fait partie d’un projet Azure Machine Learning, consultez le « **dossier Azure Machine Learning** » pour vérifier la bonne conversion de certains détails de configuration Azure Machine Learning importants comme le compte d’expérimentation, l’espace de travail ou les contextes de calcul à utiliser, etc.

1. Pour définir un fichier de démarrage, localisez le fichier dans l’Explorateur de solutions, cliquez avec le bouton droit et sélectionnez **Définir comme fichier de démarrage**.

8. Si vous le souhaitez, exécutez le programme en appuyant sur Ctrl+F5 ou en sélectionnant **Déboguer > Démarrer sans débogage**. 

> [!div class="nextstepaction"]
> [Didacticiel : Utilisation de Python dans Visual Studio](https://docs.microsoft.com/visualstudio/python/vs-tutorial-01-00)

## <a name="see-also"></a>Voir aussi

- [Création d’un environnement pour un interpréteur Python existant](https://docs.microsoft.com/visualstudio/python/python-environments#creating-an-environment-for-an-existing-interpreter)