---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d’un contr&#244;le de bo&#238;te &#224; outils WPF | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "boîte à outils"
  - "wpf"
ms.assetid: 8223c06e-f327-4778-8709-e0cc7eae2c78
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d’un contr&#244;le de bo&#238;te &#224; outils WPF
Le modèle de contrôle de boîte à outils WPF inclus dans le Kit de développement logiciel \(SDK\) Visual Studio vous permet de créer des contrôles WPF \(Windows Presentation Foundation\) qui sont automatiquement ajoutés à la **boîte à outils** quand l’extension est installée. Cette procédure pas à pas montre comment utiliser le modèle pour créer un contrôle de compteur que vous pouvez distribuer à d’autres utilisateurs.  
  
## Composants requis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel \(SDK\) Visual Studio. Pour plus d'informations, consultez [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Recherche du modèle de contrôle de boîte à outils WPF dans Visual Studio  
 Le modèle de contrôle de boîte à outils WPF est disponible dans la boîte de dialogue **Nouveau projet**, sous **Modèles installés**, aux emplacements suivants :  
  
-   **Visual Basic**, **Extensibilité**. Le langage du projet est Visual Basic.  
  
-   **Visual C\#**, **Extensibilité**. Le langage du projet est C\#.  
  
## Création d’un projet de contrôle de boîte à outils WPF  
 Le modèle de contrôle de boîte à outils WPF crée un contrôle utilisateur non défini et fournit toutes les fonctionnalités nécessaires pour ajouter le contrôle à la **boîte à outils**.  
  
#### Pour créer le projet  
  
1.  Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, sous **Modèles installés**, cliquez sur le nœud de votre langage de programmation préféré, puis sélectionnez **Extensibilité**. Dans la liste des types de projets, sélectionnez **Contrôle de boîte à outils WPF**.  
  
3.  Dans la zone **Nom**, tapez le nom que vous souhaitez utiliser pour le projet. \(Cette procédure pas à pas utilise le nom `Counter`.\) Cliquez sur **OK**.  
  
     Cela permet de créer une solution qui contient un contrôle utilisateur, un attribut pour placer le contrôle dans la **boîte à outils** et un manifeste VSIX pour le déploiement. La zone **Nom** définit le nom de la solution et le nom de l’espace de noms, mais ne définit pas le nom du contrôle tel qu’il apparaît dans la **boîte à outils**. Vous allez le définir ultérieurement dans la procédure pas à pas.  
  
### Création d’une interface utilisateur pour le contrôle  
 Le contrôle `Counter` nécessite trois contrôles enfants : deux contrôles <xref:System.Windows.Controls.Label> pour afficher le texte et le nombre actuel, et un contrôle <xref:System.Windows.Controls.Button> pour réinitialiser le nombre à 0. Aucun autre contrôle enfant n’est nécessaire, car l’hébergement d’applications augmente le compteur par programmation.  
  
##### Pour créer l’interface utilisateur  
  
1.  Dans l’**Explorateur de solutions**, double\-cliquez sur ToolboxControl.cs pour l’ouvrir dans le concepteur.  
  
     Le concepteur affiche un contrôle <xref:System.Windows.Controls.Grid> contenant un contrôle <xref:System.Windows.Controls.Button>.  
  
2.  Sélectionnez le contrôle <xref:System.Windows.Controls.Grid>, puis cliquez sur les barres bleues qui apparaissent sur les côtés supérieur et gauche de la grille pour la diviser en deux lignes et deux colonnes.  
  
3.  À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Controls.Label> vers chacune des cellules dans la ligne supérieure de la grille.  
  
     À ce stade, vous pouvez définir la disposition du contrôle en organisant les éléments sur la grille. Au lieu de cela, vous pouvez modifier directement le langage XAML \(Extensible Application Markup Language\) afin que le contrôle soit redimensionné dynamiquement pour s’adapter au texte.  
  
4.  Dans le volet **XAML**, affectez à la hauteur des éléments `RowDefinition` et la largeur des éléments `ColumnDefinition` la valeur `"auto"`.  
  
5.  Modifiez le balisage du bouton et des deux étiquettes pour ressembler à l’exemple suivant.  
  
     [!code-xml[ToolboxControlWPF#11](../misc/codesnippet/Xaml/walkthrough-creating-a-wpf-toolbox-control_1.xaml)]  
  
     Les attributs `Grid.Row` et `Grid.Column` définissent la position des éléments sur la grille. L’attribut `Grid.ColumnSpan` sur le bouton permet de redimensionner la première colonne indépendamment de la largeur du bouton.  
  
     Les attributs `Content` des étiquettes utilisent une syntaxe `{Binding}` pour établir une liaison aux propriétés que vous allez définir ultérieurement dans la procédure pas à pas.  
  
### Codage du contrôle utilisateur  
 Le contrôle `Counter` expose une méthode pour incrémenter le compteur, un événement à déclencher chaque fois que le compteur est incrémenté, un bouton `Reset` et trois propriétés pour stocker le nombre actuel, stocker le texte affiché et indiquer s’il convient d’afficher ou de masquer le bouton `Reset`. L’attribut `ProvideTolboxControl` détermine l’emplacement dans la **boîte à outils** où le contrôle `Counter` s’affiche.  
  
 Vous pouvez écrire ce contrôle de la même manière que vous écririez un contrôle Windows Forms, autrement dit en utilisant des gestionnaires d’événements et des méthodes publiques pour définir le contenu des étiquettes. Toutefois, dans WPF, vous pouvez définir un contexte de données pour le contrôle pour pouvoir lier des attributs d’élément XAML directement aux propriétés dans le code. Ce modèle fournit également une couche d’abstraction pour séparer les fonctionnalités principales de l’interface utilisateur du contrôle.  
  
 Cette procédure pas à pas montre comment créer une classe de modèle de données et lier le contexte de données du contrôle au modèle de données.  
  
##### Pour créer un modèle de données  
  
1.  Double\-cliquez sur le bouton pour ouvrir la fenêtre Code.  
  
2.  En haut du fichier, ajoutez une directive `using` pour l’espace de noms <xref:System.ComponentModel>.  
  
3.  Après la classe générée, créez une classe publique pour définir le contexte de données.  
  
     [!code-cs[ToolboxControlWPF#01](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_2.cs)]  
  
     Cette classe implémente l’interface <xref:System.ComponentModel.INotifyPropertyChanged>, qui permet de lier les éléments XAML aux propriétés définies.  
  
4.  Cliquez avec le bouton droit sur la déclaration d’interface <xref:System.ComponentModel.INotifyPropertyChanged>, cliquez sur **Implémenter l’interface**, puis à nouveau sur **Implémenter l’interface**.  
  
     Visual Studio déclare un événement `PropertyChanged`.  
  
5.  Après la déclaration d’événement, créez la méthode privée suivante pour déclencher l’événement.  
  
     [!code-cs[ToolboxControlWPF#02](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_3.cs)]  
  
6.  Créez les propriétés publiques et les champs privés suivants pour contenir les valeurs des deux étiquettes dans le contrôle.  
  
     [!code-cs[ToolboxControlWPF#03](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_4.cs)]  
  
     Avec le déclenchement de l’événement `PropertyChanged`, la liaison XAML met à jour le contenu des contrôles liés. L’affectation de la valeur `public` aux propriétés les rend disponibles pour le concepteur, mais pas pour d’autres programmes, sauf s’ils sont liés à ce contexte de données.  
  
 Maintenant que vous avez créé le modèle de données, vous pouvez implémenter la fonctionnalité code\-behind du contrôle.  
  
##### Pour implémenter le contrôle  
  
1.  Au niveau de la définition de la classe partielle qui implémente le contrôle, cliquez avec le bouton droit sur le nom de la classe, cliquez sur **Refactoriser**, sur **Renommer**, puis remplacez le nom de la classe par `Counter`. Il s’agit du nom qui s’affiche dans la **boîte à outils** quand l’extension est installée.  
  
2.  Immédiatement au\-dessus de la définition de classe, dans la déclaration d’attribut `ProvideToolboxControl`, remplacez la valeur `"Counter"` du premier paramètre par `"General"`. Le nom du groupe d’éléments qui va héberger le contrôle dans la **boîte à outils** est ainsi défini.  
  
     L’exemple suivant illustre l’attribut `ProvideToolboxControl` et la définition de classe ajustée.  
  
     [!code-cs[ToolboxControlWPF#04](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_5.cs)]  
  
3.  Créez un champ privé pour stocker le contexte de données pour le contrôle, puis assignez dans le constructeur le contexte de données à la classe `MyDataModel`, comme indiqué dans l’exemple suivant.  
  
     [!code-cs[ToolboxControlWPF#05](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_6.cs)]  
  
4.  Créez les propriétés publiques suivantes pour refléter les propriétés `Text` et `Count` du contexte de données.  
  
     [!code-cs[ToolboxControlWPF#06](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_7.cs)]  
  
     Ces propriétés mettent le contenu du contexte de données à la disposition de n’importe quelle application qui inclut le contrôle.  
  
5.  Créez la méthode publique suivante pour incrémenter le compteur, et un événement pour avertir l’application d’hébergement.  
  
     [!code-cs[ToolboxControlWPF#07](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_8.cs)]  
  
6.  Implémentez le gestionnaire d’événements Click pour le bouton `Reset` comme suit.  
  
     [!code-cs[ToolboxControlWPF#08](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_9.cs)]  
  
7.  Ajoutez la propriété publique suivante pour afficher ou masquer le bouton `Reset`.  
  
     [!code-cs[ToolboxControlWPF#09](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_10.cs)]  
  
## Test du contrôle  
 Pour tester un contrôle de **boîte à outils**, testez\-le d’abord dans l’environnement de développement, puis dans une application d’hébergement.  
  
#### Pour tester le contrôle  
  
1.  Appuyez sur F5.  
  
     Vous générez ainsi le projet et ouvrez une seconde instance de Visual Studio où le contrôle est installé.  
  
2.  Dans la nouvelle instance de Visual Studio, créez un projet d’application WPF.  
  
3.  Dans l’**Explorateur de solutions**, double\-cliquez sur MainWindow.xaml pour l’ouvrir dans le concepteur.  
  
4.  Dans la section **Général** de la **boîte à outils**, faites glisser un contrôle **Counter** vers votre formulaire, puis sélectionnez\-le.  
  
     Les propriétés `Text` et `ShowReset` doivent être affichées dans la fenêtre **Propriétés**, ainsi que les autres propriétés héritées d’<xref:System.Windows.Controls.UserControl>. La propriété `Count` ne doit pas être affichée, car elle est en lecture seule.  
  
5.  Modifiez la valeur de la propriété `Text`.  
  
     Le texte de l’étiquette qui est affiché dans le concepteur doit changer.  
  
6.  Affectez à la propriété `ShowReset` la valeur `Hidden`, puis réaffectez\-lui la valeur `Visible`.  
  
     Le bouton `Reset` sur le contrôle doit disparaître, puis réapparaître.  
  
7.  Faites glisser un contrôle <xref:System.Windows.Controls.Button> sur le formulaire, affectez à son attribut `Content``` la valeur `Test`, puis double\-cliquez sur le bouton pour ouvrir le gestionnaire d’événements Click en mode code.  
  
8.  Implémentez le gestionnaire d’événements Click pour appeler la méthode `Increment` du contrôle.  
  
     [!code-cs[ToolboxControlWPF#21](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_11.cs)]  
  
9. Dans la fonction constructeur, après l’appel à `InitializeComponent`, tapez `counter1.Implemented +=`, puis appuyez sur la touche TAB à deux reprises pour générer un gestionnaire pour l’événement `Counter.Incremented`.  
  
10. Implémentez le nouveau gestionnaire, comme indiqué dans l’exemple suivant.  
  
     [!code-cs[ToolboxControlWPF#22](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_12.cs)]  
  
11. Appuyez sur F5.  
  
     L’application WPF doit s’ouvrir.  
  
12. Cliquez sur **Test**.  
  
     Le compteur doit augmenter et le bouton doit s’atténuer légèrement.  
  
13. Cliquez sur **Test** à quatre autres reprises.  
  
     Le compteur doit augmenter et le bouton doit continuer à s’atténuer jusqu’à ce qu’il disparaisse. Si vous continuez à cliquer à l’emplacement où se trouvait le bouton, le compteur doit continuer à augmenter.  
  
14. Cliquez sur **Réinitialiser**.  
  
     Le compteur doit être réinitialisé à **0**.  
  
## Étapes suivantes  
 Quand vous générez un contrôle de **boîte à outils**, Visual Studio crée un fichier nommé *nom\_projet*.vsix dans le dossier \\bin\\debug\\ de votre projet. Vous pouvez déployer le contrôle en chargeant le fichier .vsix sur un réseau ou un site web. Quand un utilisateur ouvre le fichier .vsix, le contrôle est installé et ajouté à la **boîte à outils** Visual Studio. Vous pouvez également charger le fichier .vsix sur le site web [Galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) pour que les utilisateurs puissent le trouver en naviguant dans le **Gestionnaire d’extensions**.  
  
## Voir aussi  
 [Extension de la boîte à outils](../misc/extending-the-toolbox.md)   
 [Création d'un contrôle de boîte à outils Windows Forms](../extensibility/creating-a-windows-forms-toolbox-control.md)   
 [Extension des autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Utilisation de contrôles dans le Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6235492-b10d-4c3c-ba67-6b6a545faee1)   
 [Vue d’ensemble de la création de contrôles](../Topic/Control%20Authoring%20Overview.md)