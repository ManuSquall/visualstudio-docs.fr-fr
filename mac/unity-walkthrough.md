---
title: Bien démarrer avec la création de jeux à l’aide de Unity
description: Bien démarrer avec Unity et Visual Studio pour Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/20/2019
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.openlocfilehash: c25df777a9af10859c70741a78c880a57c6f5b8e
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984796"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Bien démarrer avec la création de jeux à l’aide de Unity dans Visual Studio pour Mac

Unity est un moteur de jeu qui vous permet de développer des jeux en C#. Cette procédure pas à pas montre comment commencer à développer et à déboguer des jeux Unity à l’aide de Visual Studio pour Mac et de l’extension Outils Visual Studio pour Mac pour Unity à côté de l’environnement Unity.

L’extension Outils Visual Studio pour Mac pour Unity est une extension gratuite, installée avec Visual Studio pour Mac. Elle permet aux développeurs Unity de tirer parti des fonctionnalités de productivité de Visual Studio pour Mac, notamment l’excellente prise en charge d’IntelliSense et les fonctionnalités de débogage, entre autres.

## <a name="objectives"></a>Objectifs

> [!div class="checklist"]
> * Découvrir le développement Unity avec Visual Studio pour Mac

## <a name="prerequisites"></a>Configuration requise

- Visual Studio pour Mac ([https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac))
- Unity 5.6.1 Personal Edition ou version ultérieure ([https://store.unity.com](https://store.unity.com/), nécessite un compte unity.com pour s’exécuter)

## <a name="intended-audience"></a>Public visé

Ce labo s’adresse aux développeurs qui connaissent C#. Une expérience approfondie n’est toutefois pas nécessaire.

## <a name="task-1-creating-a-basic-unity-project"></a>Tâche 1 : création d’un projet Unity de base

1. Lancez **Unity**. Connectez-vous si nécessaire.

2. Cliquez sur **Nouveau**.

    ![Bouton New (Nouveau) dans Unity](media/unity-image1.png)

3. Définissez **Project name** (Nom du projet) sur **« UnityLab »** et sélectionnez **3D**. Cliquez sur **Create project**.

    ![Capture d’écran de la création d’un projet](media/unity-image2.png)

4. Vous êtes maintenant face à l’interface par défaut de Unity. Elle comporte, à gauche, la hiérarchie de la scène avec les objets de jeu, au milieu, une vue 3D de la scène vide, en bas, un volet de fichiers de projet et, à droite, l’inspecteur et les services. Bien sûr, l’interface ne se limite pas à cela, mais ce sont là quelques-uns des composants les plus importants.

    ![Interface de Unity vide](media/unity-image3.png)

5. Si, en tant que développeur, vous découvrez Unity, sachez que tout ce qui s’exécute dans votre application existe dans le contexte d’une **scène**. Un fichier de scène est un fichier unique qui contient toutes sortes de métadonnées sur les ressources utilisées dans le projet pour la scène actuelle et ses propriétés. Quand vous empaquetez votre application pour une plateforme, l’application résultante est une collection d’une ou plusieurs scènes ainsi que tout code dépendant de la plateforme ajouté par vos soins. Vous pouvez avoir autant de scènes que vous le souhaitez dans un projet.

6. La nouvelle scène comporte simplement une caméra et une lumière directionnelle. Une scène nécessite une **caméra** pour les éléments qui doivent être visibles et un **écouteur audio** pour les éléments qui doivent être audibles. Ces composants sont attachés à un **GameObject**.

7. Sélectionnez l’objet **Main Camera** (Caméra principale) dans le volet **Hierarchy**.

    ![Objet Main Camera mis en évidence dans le volet Hierarchy](media/unity-image4.png)

8. Sélectionnez le volet **Inspector** à droite de la fenêtre pour consulter ses propriétés. Les propriétés de la caméra incluent les informations de transformation, l’arrière-plan, le type de projection, le champ de vision, etc. Un composant Audio Listener (écouteur audio) a également été ajouté par défaut, qui se charge essentiellement de restituer le flux audio de la scène à partir d’un microphone virtuel attaché à la caméra.

    ![Volet de l’inspecteur](media/unity-image5.png)

9. Sélectionnez l’objet **Directional Light** (Lumière directionnelle). Cet objet fournit une lumière à la scène afin que les composants tels que les shaders sachent comment effectuer le rendu des objets.

    ![Objet Direction Light (Lumière directionnelle) mis en évidence](media/unity-image6.png)

10. Utilisez l’**Inspector**, qui inclut des propriétés d’éclairage courantes, telles que le type, la couleur, l’intensité et le type d’ombre.

    ![Consultation des propriétés dans le volet Inspector](media/unity-image7.png)

11. Il est important de souligner que les projets dans Unity sont légèrement différents de leurs équivalents dans Visual Studio pour Mac. Sous l’onglet **Project** en bas, cliquez avec le bouton droit sur le dossier **Assets** (Ressources) et sélectionnez **Reveal in Finder** (Révéler dans le Finder).

    ![Action de contexte pour révéler dans le Finder](media/unity-image8.png)

12. Les projets contiennent les dossiers **Assets** (Ressources), **Library** (Bibliothèque), **ProjectSettings** (Paramètres du projet) et **Temp**, comme vous pouvez le voir. Toutefois, le seul dossier qui s’affiche dans l’interface est le dossier **Assets** (Ressources). Le dossier **Library** (Bibliothèque) est le cache local pour les ressources importées ; il conserve toutes les métadonnées des ressources. Le dossier **ProjectSettings** (Paramètres du projet) stocke des paramètres que vous pouvez configurer. Le dossier **Temp** est utilisé pour les fichiers temporaires de Mono et Unity pendant le processus de génération. Il existe également un fichier solution que vous pouvez ouvrir dans Visual Studio pour Mac (en l’occurrence, **UnityLab.sln**).

    ![Ressources dans le Finder](media/unity-image9.png)

13. Fermer la fenêtre **Finder**, puis revenez à **Unity**.

14. Le dossier **ressources** contient toutes vos ressources (art, code, audio, etc.). C’est maintenant vide, mais chaque fichier que vous ajoutez à votre projet est ici. Il s’agit toujours du dossier de niveau supérieur dans l’**éditeur Unity**. Toutefois, veillez à ajouter et à supprimer des fichiers uniquement par le biais de l’interface de Unity (ou avec Visual Studio pour Mac) ; n’utilisez jamais le système de fichiers directement.

    ![Dossiers des ressources dans Unity](media/unity-image10.png)

15. Le type **GameObject** est au cœur du développement dans Unity, car presque tout en dérive, notamment les modèles, les lumières, les systèmes de particules, etc. Ajoutez un nouvel objet **Cube** à la scène par le biais du menu **GameObject > 3D Object > Cube**.

    ![Objet Cube dans la scène](media/unity-image11.png)

16. Jetez un coup d’œil aux propriétés du nouveau **GameObject** ; comme vous pouvez le voir, il a un nom, une étiquette, un calque et une transformation. Ces propriétés sont communes à tous les **GameObjects**. En outre, plusieurs composants ont été attachés au **Cube** pour fournir les fonctionnalités nécessaires, notamment un filtre de maillage, un collider en forme de boîte et un renderer.

    ![Propriétés de l’objet de jeu](media/unity-image12.png)

17. Renommez l’objet **Cube**, qui porte le nom **« Cube »** par défaut, en **« Enemy »** . Veillez à appuyer sur **Entrée** pour enregistrer la modification. Il s’agira du cube de l’ennemi dans notre jeu simple.

    ![Propriété permettant de renommer l’objet Cube](media/unity-image13.png)

18. Ajoutez un autre objet **Cube** à la scène en suivant le même processus que ci-dessus, puis nommez cet objet **« Player »** .

    ![Renommer le second objet Cube](media/unity-image14.png)

19. Attribuez à l’objet player l’étiquette **« Player»** également (consultez le contrôle déroulant **Tag** (Étiquette) juste en dessous du champ du nom). Nous allons l’utiliser dans le script de l’ennemi pour aider à localiser l’objet de jeu player.

    ![Étiquetage de l’objet player](media/unity-image15.png)

20. Dans la vue **Scene**, éloignez l’objet player de l’objet enemy sur l’axe des Z à l’aide de la souris. Vous pouvez effectuer un déplacement le long de l’axe des Z en sélectionnant le cube par sa face **rouge** et en le faisant glisser le long de la ligne **bleue**. Étant donné que le cube réside dans un espace 3D, mais qu’il ne peut être déplacé que sur un plan 2D, l’axe le long duquel vous effectuez le glissement est particulièrement important.

    ![Vue de la scène montrant le cube](media/unity-image16.png)

21. Déplacez le cube vers le bas et vers la droite le long de l’axe. Cette action met à jour la propriété **Transform.Position** dans l’**Inspector**. Pour faciliter les étapes ultérieures dans le labo, veillez à effectuer le glissement vers un emplacement de la même manière qu’illustrée ici.

    ![Déplacement d’un cube le long de l’axe](media/unity-image17.png)

22. Vous pouvez maintenant ajouter du code pour gérer la logique de l’ennemi afin qu’elle poursuive le joueur. Cliquez avec le bouton droit sur le dossier **Assets** (Ressources) dans le panneau **Project** et sélectionnez **Create > C# Script**.

    ![Action de contexte de script C#](media/unity-image18.png)

23. Nommez le nouveau script C# **« EnemyAI »** .

    ![Script C#](media/unity-image19.png)

24. Vous pouvez attacher des scripts aux objets de jeu. En l’occurrence, faites glisser le script qui vient d’être créé vers l’objet **Enemy** dans le volet **Hierarchy**. Cet objet utilisera désormais les comportements définis dans ce script.

    ![Mise en évidence de l’ajout d’un script à un objet de jeu](media/unity-image20.png)

25. Sélectionnez **File > Save Scenes** (Fichier > Enregistrer les scènes) pour enregistrer la scène actuelle. Nommez-la **« MyScene »** .

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>Tâche 2 : utilisation des outils de Visual Studio pour Mac pour Unity

1. La meilleure façon de modifier du code C# consiste à utiliser Visual Studio pour Mac. Vous pouvez configurer Unity afin qu’il utilise Visual Studio pour Mac en tant que gestionnaire par défaut. Sélectionnez **Unity > Preferences**.

2. Sélectionnez l’onglet **outils externes** . Dans la liste déroulante **éditeur de script externe** , sélectionnez **Parcourir** , puis sélectionnez **applications/Visual Studio. app**. Vous pouvez aussi sélectionner simplement l’option **Visual Studio**, si elle est déjà présente.

    ![Onglet External Tools (Outils externes) dans les préférences](media/unity-image21.png)

3. Unity est maintenant configuré pour utiliser **Visual Studio pour Mac** pour la modification des scripts. Fermer la boîte de dialogue **Unity Preferences**.

    ![Visual Studio sélectionné dans les préférences](media/unity-image22.png)

4. Double-cliquez sur **EnemyAI.cs** pour l’ouvrir dans **Visual Studio pour Mac**.

    ![Ressource Enemy sélectionnée dans Unity](media/unity-image23.png)

5. La solution Visual Studio est simple. Elle contient un dossier **Assets** (Ressources) (le même que celui dans le **Finder**) et le script **EnemyAI.cs** créé précédemment. Dans les projets plus complexes, il est probable que la hiérarchie diffère de celle que vous voyez dans Unity.

    ![Panneau Solution dans Visual Studio pour Mac](media/unity-image24.png)

6. **EnemyAI.cs** est ouvert dans l’éditeur. Le script initial contient simplement des stubs pour les méthodes **Start** et **Update**.

7. Remplacez le code initial de l’ennemi par le code ci-dessous.

    ```csharp
    public class EnemyAI : MonoBehaviour
    {
        public float Speed = 50;
        private Transform _playerTransform;
        private Transform _myTransform;

        void Start()
        {
            var player = GameObject.FindGameObjectWithTag("Player");
            if (!player)
            {
                Debug.LogError(
                    "Could not find the main player. Ensure it has the player tag set.");
            }
            else
            {
                _playerTransform = player.transform;
            }
            _myTransform = this.transform;
        }

        void Update()
        {
            var moveAmount = Speed * Time.deltaTime;
            _myTransform.position = Vector3.MoveTowards(_myTransform.position,
                _playerTransform.position, moveAmount);

            if (_myTransform.position == _playerTransform.position)
            {
                _myTransform.position = Vector3.back * 10;
            }
        }
    }
    ```

8. Examinons rapidement le comportement simple de l’ennemi qui y est défini. Dans la méthode **Start**, nous obtenons une référence à l’objet player (par son étiquette) ainsi que sa transformation (**transform**). Dans la méthode **Update**, qui est appelée pour chaque image, l’ennemi se déplace vers l’objet player. Les mots clés et les noms utilisent un codage de couleurs pour faciliter la compréhension de la base de code dans Visual Studio pour Mac.

9. Enregistrez les modifications apportées au script de l’ennemi dans **Visual Studio pour Mac**.

## <a name="task-3-debugging-the-unity-project"></a>Tâche 3 : débogage du projet Unity

1. Définissez un point d’arrêt sur la première ligne de code dans la méthode **Start**. Vous pouvez cliquer dans la marge de l’éditeur au niveau de la ligne cible ou placer le curseur sur la ligne et appuyer sur **F9**.

    ![Définition du point d’arrêt dans Visual Studio pour Mac](media/unity-image25.png)

2. Cliquez sur le bouton **Start Debugging** (Démarrer le débogage) ou appuyez sur **F5**. Cette action génère le projet et l’attache à Unity en vue du débogage.

    ![Bouton de démarrage dans Visual Studio pour Mac](media/unity-image26.png)

3. Retournez à **Unity** et cliquez sur le bouton **Run** (Exécuter) pour démarrer le jeu.

    ![Bouton d’exécution dans Unity](media/unity-image27.png)

4. Le point d’arrêt doit être atteint et vous pouvez maintenant utiliser les outils de débogage de Visual Studio pour Mac.

    ![Point d’arrêt atteint dans Visual Studio pour Mac](media/unity-image28.png)

5. Dans le panneau **Locals** (Variables locales), recherchez le pointeur **this**, qui référence un objet **EnemyAI**. Développez la référence ; vous pouvez alors parcourir les membres associés, tels que **Speed**.

    ![Panneau de débogage des variables locales dans Visual Studio pour Mac](media/unity-image29.png)

6. Supprimez le point d’arrêt de la méthode **Start** de la même façon que vous l’avez ajouté : cliquez dessus dans la marge ou sélectionnez la ligne et appuyez sur **F9**.

    ![Point d’arrêt atteint dans Visual Studio pour Mac](media/unity-image30.png)

7. Appuyez sur **F10** pour ignorer la première ligne de code qui recherche l’objet de jeu **Player** à l’aide d’une étiquette en guise de paramètre.

8. Placez le curseur de la souris au-dessus de la variable **player** dans la fenêtre de l’éditeur de code pour voir ses membres associés. Vous pouvez même développer la superposition pour voir les propriétés enfants.

    ![Fenêtre de débogage dans l’éditeur de Visual Studio pour Mac](media/unity-image31.png)

9. Appuyez sur **F5** ou sur le bouton **Run** (Exécuter) pour continuer l’exécution. Retournez à Unity pour voir le cube de l’ennemi s’approcher à plusieurs reprises du cube du joueur. Vous devrez peut-être ajuster la caméra s’il n’est pas visible.

    ![Exécution de la scène dans Unity](media/unity-image32.png)

10. Retournez à **Visual Studio pour Mac** et définissez un point d’arrêt sur la première ligne de la méthode **Update**. Il doit être atteint immédiatement.

    ![Définition d’un point d’arrêt dans Visual Studio pour Mac](media/unity-image33.png)

11. Supposons que la vitesse est trop rapide et que nous voulons tester l’impact de la modification sans redémarrer l’application. Recherchez la variable **Speed** dans la fenêtre **Autos** (Automatique) ou **Locals**(Variables locales) et remplacez-la par **« 10 »** , puis appuyez sur **Entrée**.

    ![Ajustement des variables dans la fenêtre des variables locales](media/unity-image34.png)

12. Supprimez le point d’arrêt et appuyez sur **F5** pour reprendre l’exécution.

13. Retournez à **Unity** pour voir l’application en cours d’exécution. Le cube de l’ennemi se déplace maintenant à un cinquième de la vitesse d’origine.

    ![Fenêtre Unity avec l’application en cours d’exécution](media/unity-image35.png)

14. Arrêtez l’application Unity en recliquant sur le bouton **Run** (Exécuter).

    ![Arrêt de l’application Unity](media/unity-image36.png)

15. Retournez à **Visual Studio pour Mac**. Arrêtez la session de débogage en cliquant sur le bouton **Stop** (Arrêter).

    ![Arrêt de la session de débogage dans Visual Studio pour Mac](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>Tâche 4 : exploration des fonctionnalités Unity dans Visual Studio pour Mac

1. Visual Studio pour Mac fournit un accès rapide à la documentation Unity au sein de l’éditeur de code. Placez le curseur quelque part sur le symbole **Vector3** dans la méthode **Update** et appuyez sur **⌘ Command + '** .

    ![Sélection de la méthode dans l’éditeur de Visual Studio pour Mac](media/unity-image38.png)

2. Une nouvelle fenêtre de navigateur s’ouvre sur la documentation de **Vector3**. Fermez la fenêtre du navigateur quand vous êtes satisfait.

    ![Fenêtre de navigateur ouverte sur la documentation](media/unity-image39.png)

3. Visual Studio pour Mac fournit également des assistances qui permettent de créer rapidement des classes de comportement Unity. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Assets** (Ressources), puis sélectionnez **Add > New MonoBehaviour** (Ajouter > Nouveau MonoBehaviour).

    ![Action de contexte Nouveau MonoBehaviour](media/unity-image40.png)

4. La classe créée fournit des stubs pour les méthodes **Start** et **Update**. Après l’accolade fermante de la méthode **Update**, commencez à taper **« onmouseup »** . À mesure que vous tapez, la fonctionnalité IntelliSense de Visual Studio cerne rapidement la méthode que vous envisagez d’implémenter. Sélectionnez-la dans la liste de saisie semi-automatique proposée. Elle renseigne un stub de méthode pour vous, y compris tous les paramètres.

    ![IntelliSense dans Visual Studio pur Mac](media/unity-image41.png)

5. Dans la méthode **OnMouseUp**, tapez **« base .»** pour voir toutes les méthodes de base à appeler. Vous pouvez également explorer les différentes surcharges de chaque fonction à l’aide de l’option de navigation entre les pages dans l’angle supérieur droit du contrôle suspendu d’IntelliSense.

    ![Exploration des surcharges dans Visual Studio pour Mac](media/unity-image42.png)

6. Visual Studio pour Mac vous permet également de définir facilement de nouveaux shaders. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur **Assets** (Ressources), puis sélectionnez **Add > New Shader** (Ajouter > Nouveau Shader).

    ![Action d’ajout d’un nouveau shader dans Visual Studio pour Mac](media/unity-image43.png)

7. Grâce au traitement complet des polices et des couleurs, le format du fichier d’un shader est facile à lire et à comprendre.

    ![Mise en évidence de la syntaxe](media/unity-image44.png)

8. Retournez à **Unity**. Comme vous pouvez le constater, dans la mesure où Visual Studio pour Mac utilise le même système de projet, les modifications apportées à un des deux endroits sont automatiquement synchronisées avec l’autre. Maintenant, il est facile d’utiliser systématiquement le meilleur outil pour la tâche.

    ![Panneau des ressources dans Unity](media/unity-image45.png)

## <a name="summary"></a>Récapitulatif

Dans ce labo, vous vous êtes initié à la création d’un jeu avec Unity et Visual Studio pour Mac. Consultez[https://unity3d.com/learn](https://unity3d.com/learn) pour en savoir plus sur Unity.
