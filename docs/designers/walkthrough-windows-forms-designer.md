---
title: Tutoriel du Concepteur Windows Forms
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer, get started
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e54a0957cb6b63c95c1cd914f7fc3eb72e581ac3
ms.sourcegitcommit: 6b0503ed8d25454d6e39a8e606910b3fa58cf1d2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68981645"
---
# <a name="walkthrough-get-started-with-windows-forms-designer"></a>Procédure pas à pas : Bien démarrer avec le Concepteur Windows Forms

Le Concepteur Windows Forms fournit de nombreux outils pour la création d’applications Windows Forms. Cet article explique comment créer une application à l’aide des différents outils fournis par le concepteur, y compris les tâches suivantes :

- Organiser les contrôles à l’aide des lignes d’alignement.
- Accomplir des tâches de concepteur à l’aide de balises actives.
- Définir les marges et le remplissage des contrôles.
- Organiser les contrôles à l’aide d’un contrôle <xref:System.Windows.Forms.TableLayoutPanel>.
- Partitionner la disposition de votre contrôle à l’aide d’un contrôle <xref:System.Windows.Forms.SplitContainer>.
- Accéder à votre disposition à l’aide de la fenêtre Structure du document.
- Positionner les contrôles avec l’affichage des informations sur la taille et l’emplacement.
- Définir les valeurs des propriétés avec la fenêtre Propriétés.

Lorsque vous avez terminé, vous disposez d’un contrôle personnalisé qui a été assemblé à l’aide de la plupart des fonctionnalités de disposition disponibles dans le Concepteur Windows Forms. Ce contrôle implémente l’interface utilisateur pour une calculatrice simple. L’illustration suivante montre la disposition générale du contrôle Calculator :

![Visite guidée de l'interface utilisateur de la calculatrice](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>Créer le projet contrôle personnalisé

La première étape consiste à créer le projet de contrôle DemoCalculator.

1. Ouvrez Visual Studio et créez un projet de **bibliothèque de contrôles Windows Forms**. Nommez le projet **DemoCalculatorLib**.

   ::: moniker range=">=vs-2019"

   ![Modèle de bibliothèque de contrôles Windows Forms dans Visual Studio 2019](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. Pour renommer le fichier, dans **l’Explorateur de solutions**, sélectionnez avec le bouton droit **UserControl1.vb** ou **UserControl1.cs**, sélectionnez **Renommer**, et remplacez le nom du fichier par DemoCalculator.vb ou DemoCalculator.cs. Sélectionnez **Oui** lorsque l’on vous demande si vous souhaitez renommer toutes les références à l’élément de code « UserControl1 ».

Le Concepteur Windows Forms affiche l’aire du concepteur pour le contrôle DemoCalculator. Dans cette vue, vous pouvez concevoir graphiquement l’apparence du contrôle en sélectionnant des contrôles et des composants à partir de la boîte à outils et en les plaçant sur l’aire du concepteur. Pour plus d’informations sur les contrôles personnalisés, consultez [Variétés de contrôles personnalisés](/dotnet/framework/winforms/controls/varieties-of-custom-controls).

## <a name="design-the-control-layout"></a>Concevoir la disposition du contrôle

Le contrôle DemoCalculator contient plusieurs contrôles Windows Forms. Dans cette procédure, vous allez organiser les contrôles à l’aide du Concepteur Windows Forms.

1. Dans le Concepteur Windows Forms, modifiez le contrôle DemoCalculator en lui attribuant une plus grande taille en sélectionnant la poignée de redimensionnement dans le coin inférieur droit et en la faisant glisser vers le bas et vers la droite. Dans le coin inférieur droit de Visual Studio, recherchez les informations relatives à la taille et à l’emplacement des contrôles. Définissez la taille du contrôle sur une largeur de 500 et une hauteur de 400 en observant les informations de taille au fur et à mesure que vous redimensionnez le contrôle.

2. Dans **Boîte à outils**, sélectionnez le nœud **Conteneurs** pour l’ouvrir. Sélectionnez le contrôle **SplitContainer** et faites-le glisser sur l’aire du concepteur.

   `SplitContainer` est placé sur l’aire du concepteur du contrôle DemoCalculator.

    > [!TIP]
    > Le contrôle `SplitContainer` se redimensionne en fonction de la taille du contrôle DemoCalculator. Examinez la fenêtre **Propriétés** pour afficher les paramètres de propriété du contrôle `SplitContainer`. Recherchez la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A>. Sa valeur est [DockStyle.Fill](xref:System.Windows.Forms.DockStyle.Fill), ce qui signifie que le contrôle `SplitContainer` se dimensionnera toujours selon les limites du contrôle DemoCalculator. Redimensionnez le contrôle DemoCalculator pour vérifier ce comportement.

3. Dans la fenêtre **Propriétés**, remplacez la valeur de la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A>par `None`.

    Le contrôle `SplitContainer` est réduit à sa taille par défaut et ne suit plus la taille du contrôle DemoCalculator.

4. Sélectionnez le glyphe d’étiquette active (![Glyphe d’étiquette active](media/smart-tag-glyph.gif)) dans le coin supérieur droit du contrôle `SplitContainer`. Sélectionnez **Ancrer dans le conteneur parent** pour définir la propriété `Dock` sur `Fill`.

    Le contrôle `SplitContainer` s’ancre sur les limites du contrôle DemoCalculator.

    > [!NOTE]
    > Plusieurs contrôles offrent des balises actives pour faciliter la conception. Pour plus d’informations, consultez [Procédure pas à pas : Exécuter des tâches courantes à l’aide de balises actives dans les contrôles Windows Forms](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls).

5. Sélectionnez la bordure verticale entre les panneaux et faites-la glisser vers la droite, afin que la plus grande partie de l’espace soit prise par le panneau gauche.

    `SplitContainer` divise le contrôle DemoCalculator en deux panneaux avec une bordure mobile qui les sépare. Le panneau de gauche contient les boutons et l’affichage de la calculatrice, et le panneau à droite affiche un enregistrement des opérations arithmétiques effectuées par l’utilisateur.

6. Dans la fenêtre **Propriétés**, remplacez la valeur de la propriété `BorderStyle`par `Fixed3D`.

7. Dans **Boîte à outils**, sélectionnez le nœud **Contrôles courants** pour l’ouvrir. Sélectionnez le contrôle `ListView` et faites-le glisser dans le volet droit du contrôle `SplitContainer`.

8. Sélectionnez le glyphe de balise active du contrôle `ListView`. Dans le panneau des balises actives, remplacez le paramètre `View` par `Details`.

9. Dans le panneau des balises actives, sélectionnez **Modifier les colonnes**.

   La boîte de dialogue **Éditeur de collections ColumnHeader** s’ouvre.

10. Dans la boîte de dialogue **Éditeur de collections ColumnHeader**, sélectionnez **Ajouter** pour ajouter une colonne au contrôle `ListView`. Remplacez la valeur de la propriété `Text` de la colonne par **Historique**. Sélectionnez **OK** pour créer la colonne.

11. Dans le panneau des balises actives, sélectionnez **Ancrer dans le conteneur parent**, puis sélectionnez le glyphe de balise active pour fermer le panneau des balises actives.

12. À partir de **Boîte à outils** pour le nœud **Conteneurs**, faites glisser un contrôle `TableLayoutPanel` dans le panneau gauche du contrôle `SplitContainer`.

    Le contrôle `TableLayoutPanel` apparaît sur l’aire du concepteur avec son panneau des balises actives ouvert. Le contrôle `TableLayoutPanel` réorganise ses contrôles enfants dans une grille. Le contrôle `TableLayoutPanel` contiendra l’affichage et les boutons du contrôle DemoCalculator. Pour plus d’informations, consultez [Procédure pas à pas : Organiser les contrôles à l’aide d’un TableLayoutPanel](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel).

13. Sélectionnez **Modifier les lignes et les colonnes** dans le panneau des balises actives.

    La boîte de dialogue **Styles de lignes et de colonnes** s’ouvre.

14. Sélectionnez le bouton **Ajouter** jusqu’à ce que cinq colonnes s’affichent. Sélectionnez les cinq colonnes, puis sélectionnez **Pourcentage** dans la zone **Type de taille**. Définissez la valeur **Pourcentage** sur **20**. Cette valeur définit chaque colonne sur la même largeur.

15. Sous **Afficher**, sélectionnez **Lignes**.

16. Sélectionnez **Ajouter** jusqu’à ce que cinq lignes s’affichent. Sélectionnez les cinq lignes, puis sélectionnez **Pourcentage** dans la zone **Type de taille**. Définissez la valeur **Pourcentage** sur **20**. Cette valeur définit chaque ligne sur la même hauteur.

17. Sélectionnez **OK** pour accepter vos modifications, puis sélectionnez le glyphe de balise active pour fermer le panneau des balises actives.

18. Dans la fenêtre **Propriétés**, remplacez la valeur de la propriété `Dock`par `Fill`.

## <a name="populate-the-control"></a>Remplir le contrôle

Maintenant que la disposition du contrôle est configurée, vous pouvez remplir le contrôle DemoCalculator avec des boutons et un affichage.

1. Dans **Boîte à outils**, double-cliquez sur l’icône du contrôle `TextBox`.

   Un contrôle `TextBox` est placé dans la première cellule du contrôle `TableLayoutPanel`.

2. Dans la fenêtre **Propriétés**, remplacez la valeur de la propriété ColumnSpan du contrôle `TextBox` par **5**.

   Le contrôle `TextBox` se déplace vers une position centrée sur sa ligne.

3. Remplacez la valeur de la propriété `Anchor` du contrôle `TextBox` par `Left`, `Right`.

   Le contrôle `TextBox` se développe horizontalement pour couvrir les cinq colonnes.

4. Affectez la valeur `TextBox` à la propriété `TextAlign` du contrôle `Right`.

5. Dans la fenêtre **Propriétés**, développez le nœud de la propriété `Font`. Définissez `Size` sur **14**, et définissez `Bold` sur **true** pour le contrôle `TextBox`.

6. Sélectionnez le contrôle `TableLayoutPanel`.

7. Dans **Boîte à outils**, double-cliquez sur l’icône `Button`.

   Un contrôle `Button` est placé dans la cellule ouverte suivante du contrôle `TableLayoutPanel`.

8. Dans **Boîte à outils**, double-cliquez sur l’icône `Button` quatre fois pour remplir la deuxième ligne du contrôle `TableLayoutPanel`.

9. Sélectionnez les cinq contrôles `Button` en les sélectionnant tout en maintenant la touche **Maj** enfoncée. Appuyez sur **Ctrl**+**C** pour copier les contrôles `Button` dans le presse-papiers.

10. Appuyez sur **Ctrl**+**V** trois fois pour coller les copies des contrôles `Button` dans les lignes restantes du contrôle `TableLayoutPanel`.

11. Sélectionnez les 20 contrôles `Button` en les sélectionnant tout en maintenant la touche **Maj** enfoncée.

12. Dans la fenêtre **Propriétés**, remplacez la valeur de la propriété `Dock`par `Fill`.

    Tous les contrôles `Button` s’ancrent pour remplir leurs cellules contenantes.

13. Dans la fenêtre **Propriétés**, développez le nœud de la propriété `Margin`. Définissez la valeur de `All` sur **5**.

    Tous les contrôles `Button` sont de taille inférieure pour créer une marge plus grande entre eux.

14. Sélectionnez **button10** et **button20**, et appuyez sur **Supprimer** pour les supprimer de la disposition.

15. Sélectionnez **button5** et **button15**, puis remplacez la valeur de leur propriété `RowSpan` par **2**. Ceux-ci seront les boutons **Effacer** et **=** pour le contrôle DemoCalculator.

## <a name="use-the-document-outline-window"></a>Utiliser la fenêtre Structure du document

Lorsque votre contrôle ou formulaire est rempli avec plusieurs contrôles, il peut s’avérer plus facile de naviguer dans votre disposition avec la fenêtre Structure du document.

1. Dans la barre de menus, choisissez **Affichage** > **Autres fenêtres** > **Structure du document**.

   La fenêtre Structure du document affiche une arborescence du contrôle DemoCalculator et de ses contrôles constitutifs. Les contrôles de conteneur comme `SplitContainer` affichent leurs contrôles enfants comme sous-nœuds dans l’arborescence. Vous pouvez également renommer les contrôles en place à l’aide de la fenêtre Structure du document.

2. Dans la fenêtre **Structure du document**, cliquez avec le bouton droit sur **button1**, puis sélectionnez **Renommer**. Remplacez son nom par sevenButton.

3. À l’aide de la fenêtre **Structure du document**, remplacez le nom généré par le concepteur des contrôles `Button` par le nom de production en fonction de la liste suivante :

   - button1 renommé **sevenButton**

   - button2 renommé **eightButton**

   - button3 renommé **nineButton**

   - button4 renommé **divisionButton**

   - button5 renommé **clearButton**

   - button6 renommé **fourButton**

   - button7 renommé **fiveButton**

   - button8 renommé **sixButton**

   - button9 renommé **multiplicationButton**

   - button11 renommé **oneButton**

   - button12 renommé **twoButton**

   - button13 renommé **threeButton**

   - button14 renommé **subtractionButton**

   - button15 renommé **equalsButton**

   - button16 renommé **zeroButton**

   - button17 renommé **changeSignButton**

   - button18 renommé **decimalButton**

   - button19 renommé **additionButton**

4. À l’aide des fenêtres **Structure du document** et **Propriétés**, modifiez la valeur de la propriété `Text` pour chaque nom de contrôle `Button` en fonction de la liste suivante :

   - Remplacez la propriété texte du contrôle sevenButton par **7**

   - Remplacez la propriété texte du contrôle eightButton par **8**

   - Remplacez la propriété texte du contrôle nineButton par **9**

   - Remplacez la propriété texte du contrôle divisionButton par **/** (barre oblique avant)

   - Remplacez la propriété texte du contrôle clearButton par **Clear**

   - Remplacez la propriété texte du contrôle fourButton par **4**

   - Remplacez la propriété texte du contrôle fiveButton par **5**

   - Remplacez la propriété texte du contrôle sixButton par **6**

   - Remplacez la propriété texte du contrôle multiplicationButton par **\*** (astérisque)

   - Remplacez la propriété texte du contrôle oneButton par **1**

   - Remplacez la propriété texte du contrôle twoButton par **2**

   - Remplacez la propriété texte du contrôle threeButton par **3**

   - Remplacez la propriété texte du contrôle subtractionButton par **-** (trait d’union)

   - Remplacez la propriété texte du contrôle equalsButton par **=** (signe égal)

   - Remplacez la propriété texte du contrôle zeroButton par **0**

   - Remplacez la propriété texte du contrôle changeSignButton par **+/-**

   - Remplacez la propriété texte du contrôle decimalButton par **.** (point)

   - Remplacez la propriété texte du contrôle additionButton par **+** (signe plus)

5. Dans l’aire du concepteur, sélectionnez tous les contrôles `Button` en les sélectionnant tout en maintenant la touche **Maj** enfoncée.

6. Dans la fenêtre **Propriétés**, développez le nœud de la propriété `Font`. Définissez `Size` sur **14**, et définissez `Bold` sur **true** pour tous les contrôles `Button`.

Cela termine la conception du contrôle DemoCalculator. Il ne reste plus qu’à fournir la logique de la calculatrice.

## <a name="implement-event-handlers"></a>Implémenter les gestionnaires d'événements

Les boutons du contrôle DemoCalculator ont des gestionnaires d’événements qui peuvent être utilisés pour implémenter une bonne partie de la logique de la calculatrice. Le Concepteur Windows Forms vous permet d’implémenter les stubs de tous les gestionnaires d’événements pour tous les boutons avec un double-clic.

1. Dans l’aire du concepteur, sélectionnez tous les contrôles `Button` en les sélectionnant tout en maintenant la touche **Maj** enfoncée.

2. Double-cliquez sur l’un des contrôles `Button`.

   L’éditeur de code s’ouvre sur les gestionnaires d’événements générés par le concepteur.

## <a name="test-the-control"></a>Tester le contrôle

Étant donné que le contrôle DemoCalculator hérite de la classe <xref:System.Windows.Forms.UserControl>, vous pouvez tester son comportement avec le **Conteneur de test UserControl**. Pour plus d'informations, voir [Procédure : Tester le comportement au moment de l’exécution d’un UserControl](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol).

1. Appuyez sur **F5** pour générer et exécuter le contrôle DemoCalculator dans le **Conteneur de test UserControl**.

2. Sélectionnez la bordure entre les panneaux `SplitContainer` et faites-la glisser vers la gauche et la droite. `TableLayoutPanel` et tous ses contrôles enfants se redimensionnent pour s’ajuster à l’espace disponible.

3. Lorsque vous avez terminé de tester le contrôle, sélectionnez **Fermer**.

## <a name="use-the-control-on-a-form"></a>Utiliser le contrôle sur un formulaire

Le contrôle DemoCalculator peut être utilisé dans d’autres contrôles composites ou sur un formulaire. La procédure suivante explique comment l’utiliser.

### <a name="create-the-project"></a>Créer le projet

La première étape consiste à créer le projet d’application. Vous utiliserez ce projet pour générer l’application qui affiche votre contrôle personnalisé.

1. Créez un projet **Application Windows Forms** et nommez-le **DemoCalculatorTest**.

2. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet **DemoCalculatorTest**, puis sélectionnez **Ajouter une référence** pour ouvrir la boîte de dialogue **Ajouter une référence**.

3. Sélectionnez l’onglet **Projets**, puis double-cliquez sur le projet DemoCalculatorLib pour ajouter la référence au projet de test.

4. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **DemoCalculatorTest**, puis sélectionnez **Définir comme projet de démarrage**.

5. Dans le Concepteur Windows Forms, augmentez la taille du formulaire à environ **700 x 500**.

### <a name="use-the-control-in-the-forms-layout"></a>Utiliser le contrôle dans la disposition du formulaire

Pour utiliser le contrôle DemoCalculator dans une application, vous devez le placer sur un formulaire.

1. Dans **Boîte à outils**, développez le nœud **Composants DemoCalculatorLib**.

2. Faites glisser le contrôle **DemoCalculator** de **Boîte à outils** vers votre formulaire. Déplacez le contrôle dans le coin supérieur gauche du formulaire. Lorsque le contrôle est proche des bordures du formulaire, des *lignes d’alignement* s’affichent. Les lignes d’alignement indiquent la distance entre la propriété `Padding` du formulaire et la propriété `Margin` du contrôle. Positionnez le contrôle à l’emplacement indiqué par les lignes d’alignement.

   Pour plus d’informations, consultez [Procédure pas à pas : Organiser les contrôles à l’aide des lignes d’alignement](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines).

3. Faites glisser un contrôle `Button` à partir de **Boîte à outils** et déposez-le sur le formulaire.

4. Déplacez le contrôle `Button` autour du contrôle DemoCalculator et observez où les lignes d’alignement s’affichent. Vous pouvez aligner vos contrôles avec précision et en toute simplicité à l’aide de cette fonctionnalité. Supprimez le contrôle `Button` lorsque vous avez terminé.

5. Sélectionnez avec le bouton droit le contrôle DemoCalculator, puis sélectionnez **Propriétés**.

6. Remplacez la valeur de la propriété `Dock` par `Fill`.

7. Sélectionnez le formulaire, puis développez le nœud de la propriété `Padding`. Remplacez la valeur de **Tous** par **20**.

   La taille du contrôle DemoCalculator est réduite pour s’adapter à la nouvelle valeur `Padding` du formulaire.

8. Redimensionnez le formulaire en faisant glisser les diverses poignées de redimensionnement à différentes positions. Observez comment le contrôle DemoCalculator est redimensionné pour s’adapter.

## <a name="next-steps"></a>Étapes suivantes

Cet article a montré comment construire l’interface utilisateur pour une calculatrice simple. Pour continuer, vous pouvez étendre ses fonctionnalités en implémentant la logique de calculatrice. Ou passez à un autre tutoriel dans lequel vous [créez une visionneuse d’images à l’aide de Windows Forms](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Voir aussi

- [Accessibilité des contrôles Windows Forms](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)