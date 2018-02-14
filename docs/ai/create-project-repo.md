---
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Cloner un dépôt de code Python dans Visual Studio

Une fois que vous avez [installé Visual Studio Tools pour IA](installation.md), vous pouvez facilement cloner un dépôt de code Python et créer un projet à partir de celui-ci.

1. Pour vous connecter à des dépôts GitHub, exécutez le programme d’installation de Visual Studio, sélectionnez **Modifier**, puis sélectionnez l’onglet **Composants individuels**. Faites défiler jusqu’à la section **Outils de code**, sélectionnez **Extension GitHub pour Visual Studio**, puis sélectionnez **Modifier**.
    
    ![Sélection de l’extension GitHub dans le programme d’installation de Visual Studio](media\create-project-repo\installation-github-extension.png)
    
2. Lancez Visual Studio.

3. Sélectionnez **Affichage > Team Explorer...** pour ouvrir la fenêtre **Team Explorer**, dans laquelle vous pouvez vous connecter à GitHub ou à Visual Studio Team Services, ou cloner un dépôt.

    ![Fenêtre Team Explorer montrant Visual Studio Team Services, GitHub et le clonage d’un dépôt](media\create-project-repo\team-explorer.png)

4. Dans le champ URL, sous **Dépôts Git locaux**, entrez `https://github.com/Microsoft/samples-for-ai`, entrez un dossier pour les fichiers clonés, puis sélectionnez **Cloner**.

    > [!Tip]
    > Le dossier que vous spécifiez dans Team Explorer est le dossier spécifique pour recevoir les fichiers clonés. Contrairement à la commande `git clone`, la création d’un clone dans Team Explorer ne crée pas automatiquement un sous-dossier avec le nom du dépôt.

5. Quand le clonage est terminé, double-cliquez sur le dossier du dépôt dans le bas de Team Explorer pour accéder au tableau de bord du dépôt. Sous **Solutions**, sélectionnez **Nouveau...**.

    ![Fenêtre Team Explorer, création d’un projet à partir d’un clone](media\create-project-repo\team-explorer-new-project.png)

6. Dans la boîte de dialogue **Nouveau projet** qui s’affiche, sélectionnez « **À partir de code Python existant** », spécifiez un nom pour le projet, définissez **Emplacement** sur le même dossier que le dépôt, puis sélectionnez **OK**. Dans l’Assistant qui apparaît, sélectionnez **Terminer**.

7. Sélectionnez **Affichage > Explorateur de solutions** dans le menu.

8. Dans l’Explorateur de solutions, développez le nœud `TensorFlow Examples> MNIST`, cliquez avec le bouton droit sur `convolutional.py`, puis sélectionnez **Définir comme fichier de démarrage**. Cette étape indique à Visual Studio quel fichier utiliser quand vous exécutez le projet.

10. Appuyez sur Ctrl+F5 ou sélectionnez **Déboguer > Démarrer sans débogage** pour exécuter le programme. Si vous voyez une `, revérifiez la valeur du répertoire de travail de l’étape précédente.


11. Lorsque le programme s’exécute correctement, vous le voyez commencer à télécharger votre jeu de données d’apprentissage et de test, puis effectuer l’apprentissage du modèle et générer votre taux d’erreur. Vous voulez que le taux d’erreur diminue au fil du temps

    ![Première sortie du programme Python MNIST](media\create-project-repo\tensorflow-mnist-running.png)

> Si vous utilisez Anaconda et obtenez une erreur relative à l’absence de numpy, vous devrez peut-être [modifier votre environnement python pour utiliser Anaconda](../python/managing-python-environments-in-visual-studio.md).

11. Vous pouvez visualiser la progression avec TensorBoard. Cliquez avec le bouton droit sur votre projet et cliquez sur **Exécuter TensorBoard**, puis sélectionnez le répertoire de vos journaux TensorBoard de sortie.

    ![exécuter tensorboard](media\create-project-repo\run-tensorboard.png)

11. Remarquer que l’erreur diminue au fil du temps, ce qui signifie que la qualité s’améliore

    ![exécuter tensorboard](media\create-project-repo\tensorboard.png)