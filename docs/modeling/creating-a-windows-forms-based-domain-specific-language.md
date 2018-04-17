---
title: Création d’un langage spécifique à un domaine Windows Forms | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 23fe0d582f92d5025049974ccd64357203e4845a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Création d'un langage spécifique à un domaine basé sur Windows Forms
Vous pouvez utiliser Windows Forms pour afficher l’état d’un modèle de langage de spécifique à un domaine (DSL), au lieu d’utiliser un diagramme DSL. Cette rubrique vous guide dans la liaison d’un Windows Form à DSL, à l’aide de la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK.  
  
 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
Une instance DSL, affichant une interface utilisateur du formulaire Windows et l’Explorateur de modèles.  
  
## <a name="creating-a-windows-forms-dsl"></a>Création d’un Windows Forms DSL  
 Le **minimale WinForm concepteur** les modèle DSL crée une DSL minimale que vous pouvez modifier pour l’adapter à vos propres exigences.  
  
#### <a name="to-create-a-minimal-winforms-dsl"></a>Pour créer un DSL WinForms minimale  
  
1.  Créer une DSL à partir de la **minimale WinForm concepteur** modèle.  
  
     Dans cette procédure pas à pas, les noms suivants sont supposés :  
  
    |||  
    |-|-|  
    |Nom de solution et DSL|FarmApp|  
    |Espace de noms|Company.FarmApp|  
  
2.  Faire des essais avec l’exemple initial fournies par le modèle :  
  
    1.  Transformer tous les modèles.  
  
    2.  Générer et exécuter l’exemple (**CTRL + F5**).  
  
    3.  Dans l’instance expérimentale de Visual Studio, ouvrez le `Sample` fichier dans le projet de débogage.  
  
         Notez qu’il s’affiche dans un contrôle Windows Forms.  
  
         Vous pouvez également voir les éléments du modèle affiché dans l’Explorateur.  
  
         Ajouter des éléments dans le formulaire ou de l’Explorateur et notez qu’elles apparaissent dans l’affichage des autres.  
  
 Dans l’instance principale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], notez les points suivants concernant la solution DSL :  
  
-   `DslDefinition.dsl` ne contient aucun élément de diagramme. Il s’agit, car vous n’utiliserez pas les diagrammes DSL pour afficher les modèles d’instance de cette DSL. Au lieu de cela, vous allez lier un Windows Form au modèle et les éléments sur le formulaire affiche le modèle.  
  
-   Outre la `Dsl` et `DslPackage` projets, la solution contient un troisième projet nommé `UI.` **UI** projet contient la définition d’un contrôle Windows Forms. `DslPackage` dépend de `UI`, et `UI` dépend `Dsl`.  
  
-   Dans le `DslPackage` projet, `UI\DocView.cs` contient le code qui affiche le contrôle Windows Forms qui est défini dans le `UI` projet.  
  
-   Le `UI` projet contient un exemple fonctionnel d’un contrôle de formulaire lié à la DSL. Toutefois, il ne fonctionne pas lorsque vous avez modifié la définition DSL. Le `UI` projet contient :  
  
    -   Une classe Windows Forms nommée `ModelViewControl`.  
  
    -   Un fichier nommé `DataBinding.cs` qui contient une définition partielle supplémentaire de `ModelViewControl`. Pour afficher son contenu, dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le fichier et choisissez **afficher le Code**.  
  
### <a name="about-the-ui-project"></a>Sur le projet d’interface utilisateur  
 Lorsque vous mettez à jour le fichier de définition DSL pour définir votre propre DSL, vous devrez mettre à jour le contrôle dans le `UI` projet pour afficher votre DSL. Contrairement à la `Dsl` et `DslPackage` de projets, l’exemple `UI` projet n’est pas généré à partir de `DslDefinitionl.dsl`. Vous pouvez ajouter des fichiers .tt pour générer le code si vous le souhaitez, mais qui n’est pas abordé dans cette procédure pas à pas.  
  
## <a name="updating-the-dsl-definition"></a>Mise à jour la définition DSL  
 Suit que la définition DSL est utilisée dans cette procédure pas à pas.  
  
 ![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png "DSL-Wpf-1")  
  
#### <a name="to-update-the-dsl-definition"></a>Pour mettre à jour la définition DSL  
  
1.  Ouvrez DslDefinition.dsl dans le concepteur DSL.  
  
2.  Supprimer **ExampleElement**  
  
3.  Renommer le **ExampleModel** classe de domaine à `Farm`.  
  
     Lui donner des propriétés de domaine supplémentaire nommées `Size` de type **Int32**, et `IsOrganic` de type **booléenne**.  
  
    > [!NOTE]
    >  Si vous supprimez la classe de domaine racine et puis créez une nouvelle racine, vous devez réinitialiser la propriété de classe racine de l’éditeur. Dans **Explorateur DSL**, sélectionnez **éditeur**. Puis, dans la fenêtre Propriétés, définissez **classe racine** à `Farm`.  
  
4.  Utilisez le **classe de domaine nommé** outil pour créer les classes de domaine suivantes :  
  
    -   `Field` -Définir une propriété de domaine supplémentaire nommée `Size`.  
  
    -   `Animal` -Dans la fenêtre Propriétés, définissez **modificateur d’héritage** à **abstraite**.  
  
5.  Utilisez le **classe de domaine** outil pour créer les classes suivantes :  
  
    -   `Sheep`  
  
    -   `Goat`  
  
6.  Utilisez le **héritage** outil `Goat` et `Sheep` hériter `Animal`.  
  
7.  Utilisez le **Embedding** outil pour incorporer `Field` et `Animal` sous `Farm`.  
  
8.  Vous souhaiterez peut-être vider le diagramme. Pour réduire le nombre d’éléments en double, utilisez le **mettre la sous-arborescence ici** du menu contextuel des éléments de la feuille.  
  
9. **Transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions.  
  
10. Générer le **Dsl** projet.  
  
    > [!NOTE]
    >  À ce stade, les autres projets ne seront pas généré sans erreur. Toutefois, nous souhaitons générer le projet Dsl afin que son assembly est disponible dans l’Assistant Source de données.  
  
## <a name="updating-the-ui-project"></a>Mise à jour le projet de l’interface utilisateur  
 Vous pouvez maintenant créer un nouveau contrôle utilisateur qui affiche les informations stockées dans le modèle DSL. Pour connecter le contrôle utilisateur pour le modèle le plus simple est par le biais des liaisons de données. La liaison de type adaptateur nommé données **ModelingBindingSource** est spécifiquement conçu pour se connecter DSL à des interfaces non-VMSDK.  
  
#### <a name="to-define-your-dsl-model-as-a-data-source"></a>Pour définir votre modèle DSL comme source de données  
  
1.  Sur le **données** menu, choisissez **afficher les Sources de données**.  
  
     Le **des Sources de données** fenêtre s’ouvre.  
  
     Choisissez **ajouter une nouvelle Source de données**. Le **Assistant de Configuration de Source de données** s’ouvre.  
  
2.  Choisissez **objet**, **suivant**.  
  
     Développez **Dsl**, **Company.FarmApp**, puis sélectionnez **batterie**, qui est la classe racine de votre modèle. Choisissez **Terminer**.  
  
     Dans l’Explorateur de solutions, le **UI** projet contient désormais **Properties\DataSources\Farm.datasource**  
  
     Les propriétés et les relations de votre classe de modèle s’affichent dans la fenêtre Sources de données.  
  
     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png "DslWpf-3")  
  
#### <a name="to-connect-your-model-to-a-form"></a>Pour se connecter de votre modèle à un formulaire  
  
1.  Dans le **UI** projet d’équipe, supprimez tous les fichiers .cs existant.  
  
2.  Ajouter un nouveau **contrôle utilisateur** fichier nommé `FarmControl` à la **UI** projet.  
  
3.  Dans le **des Sources de données** fenêtre, dans le menu déroulant sur **batterie**, choisissez **détails**.  
  
     Conservez les paramètres par défaut pour les autres propriétés.  
  
4.  Ouvrez FarmControl.cs en mode design.  
  
     Faites glisser **batterie** à partir de la fenêtre Sources de données sur FarmControl.  
  
     Un ensemble de contrôles apparaît, une pour chaque propriété. Propriétés de relation ne génèrent pas de contrôles.  
  
5.  Supprimer **farmBindingNavigator**. Cela est également générée automatiquement dans le `FarmControl` concepteur, mais il n’est pas utile pour cette application.  
  
6.  À l’aide de la boîte à outils, créez deux instances de **DataGridView**et nommez-les `AnimalGridView` et `FieldGridView`.  
  
    > [!NOTE]
    >  Une autre consiste à faire glisser les éléments d’animaux et les champs à partir de la fenêtre Sources de données sur le contrôle. Cette action crée automatiquement des grilles de données et liaisons entre l’affichage de grille et de la source de données. Toutefois, cette liaison ne fonctionne pas correctement pour DSL. Par conséquent, il est préférable de créer les grilles de données et les liaisons manuellement.  
  
7.  Si la boîte à outils ne contient-elle pas le **ModelingBindingSource** outil, ajoutez-le. Dans le menu contextuel de la **données** , onglet choisir **choisir des éléments de**. Dans le **choisir des éléments de boîte à outils** boîte de dialogue, sélectionnez **ModelingBindingSource** à partir de la **onglet .NET Framework**.  
  
8.  À l’aide de la boîte à outils, créez deux instances de **ModelingBindingSource**et nommez-les `AnimalBinding` et `FieldBinding`.  
  
9. Définir le **DataSource** propriété de chaque **ModelingBindingSource** à **farmBindingSource**.  
  
     Définir le **DataMember** propriété **animaux** ou **champs**.  
  
10. Définir le **DataSource** propriétés de `AnimalGridView` à `AnimalBinding`et de `FieldGridView` à `FieldBinding`.  
  
11. Ajuster la disposition du contrôle à votre batterie de serveurs.  
  
 Le **ModelingBindingSource** est un adaptateur qui remplit plusieurs fonctions qui sont spécifiques à DSL :  
  
-   Elle encapsule les mises à jour dans une Transaction de magasin VMSDK.  
  
     Par exemple, lorsque l’utilisateur supprime une ligne à partir de la grille de vue de données, une liaison régulière entraînerait une exception de transaction.  
  
-   Elle garantit que, lorsque l’utilisateur sélectionne une ligne, la fenêtre Propriétés affiche les propriétés de l’élément de modèle correspondant, au lieu de la ligne de grille de données.  
  
 ![DslWpf4](../modeling/media/dslwpf4.png "DslWpf4")  
Schéma des liens entre des sources de données et les vues.  
  
#### <a name="to-complete-the-bindings-to-the-dsl"></a>Pour terminer les liaisons du DSL  
  
1.  Ajoutez le code suivant dans un fichier de code séparé dans le **UI** projet :  
  
    ```csharp  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  
  
    namespace Company.FarmApp  
    {  
      partial class FarmControl  
      {  
        public IContainer Components { get { return components; } }  
  
        /// <summary>Binds the WinForms data source to the DSL model.  
        /// </summary>  
        /// <param name="nodelRoot">The root element of the model.</param>  
        public void DataBind(ModelElement modelRoot)  
        {  
          WinFormsDataBindingHelper.PreInitializeDataSources(this);  
          this.farmBindingSource.DataSource = modelRoot;  
          WinFormsDataBindingHelper.InitializeDataSources(this);  
        }  
      }  
    }  
    ```  
  
2.  Dans le **DslPackage** projet, modifier **DslPackage\DocView.tt** pour mettre à jour la définition de la variable suivante :  
  
    ```csharp  
    string viewControlTypeName = "FarmControl";  
    ```  
  
## <a name="testing-the-dsl"></a>Test du DSL  
 La solution DSL permettre maintenant générer et exécuter, bien que vous souhaiterez peut-être ajouter d’autres améliorations ultérieurement.  
  
#### <a name="to-test-the-dsl"></a>Pour tester la DSL  
  
1.  Générez et exécutez la solution.  
  
2.  Dans l’instance expérimentale de Visual Studio, ouvrez le **exemple** fichier.  
  
3.  Dans le **FarmApp Explorer**, ouvrez le menu contextuel sur le **batterie** nœud racine, puis choisissez **ajouter un nouveau chèvre**.  
  
     `Goat1` s’affiche dans le **animaux** vue.  
  
    > [!WARNING]
    >  Vous devez utiliser le menu contextuel sur le **batterie** nœud, pas le **animaux** nœud.  
  
4.  Sélectionnez le **batterie** nœud racine et afficher ses propriétés.  
  
     Dans l’affichage du formulaire, modifiez le **nom** ou **taille** de la batterie de serveurs.  
  
     Lorsque vous quittez chaque champ dans le formulaire, les modifications apportées aux propriétés correspondantes dans la fenêtre Propriétés.  
  
## <a name="enhancing-the-dsl"></a>Amélioration du DSL  
  
#### <a name="to-make-the-properties-update-immediately"></a>Pour rendre les propriétés à mettre à jour immédiatement  
  
1.  Dans la vue de conception de FarmControl.cs, sélectionnez un champ simple comme nom, une taille ou IsOrganic.  
  
2.  Dans la fenêtre Propriétés, développez **DataBindings** et ouvrez **(Avancé)**.  
  
     Dans le **mise en forme et liaison avancée** boîte de dialogue, sous **Mode de mise à jour de Source de données**, choisissez **OnPropertyChanged**.  
  
3.  Générez et exécutez la solution.  
  
     Vérifiez que lorsque vous modifiez le contenu du champ, la propriété correspondante d’immédiatement les modifications du modèle de batterie de serveurs.  
  
#### <a name="to-provide-add-buttons"></a>Pour fournir des boutons Ajouter  
  
1.  Dans la vue de conception de FarmControl.cs, utilisez la boîte à outils pour créer un bouton sur le formulaire.  
  
     Modifier le nom et le texte du bouton, par exemple pour `New Sheep`.  
  
2.  Ouvrez le code derrière le bouton (par exemple en double-cliquant dessus).  
  
     Modifier comme suit :  
  
    ```csharp  
    private void NewSheepButton_Click(object sender, EventArgs e)  
    {  
      using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
      {  
        elementOperations.MergeElementGroup(farm,  
          new ElementGroup(new Sheep(farm.Partition)));  
        t.Commit();  
      }  
    }  
  
    // The following code is shared with other add buttons:  
    private ElementOperations operationsCache = null;  
    private ElementOperations elementOperations  
    {  
      get  
      {  
        if (operationsCache == null)  
        {  
          operationsCache = new ElementOperations(farm.Store, farm.Partition);  
        }  
        return operationsCache;  
      }  
    }  
    private Farm farm  
    {  
      get { return this.farmBindingSource.DataSource as Farm; }  
    }  
  
    ```  
  
     Vous devrez également insérer la directive suivante :  
  
    ```csharp  
  
    using Microsoft.VisualStudio.Modeling;  
  
    ```  
  
3.  Ajouter des boutons similaires de caprins et les champs.  
  
4.  Générez et exécutez la solution.  
  
5.  Vérifiez que le bouton Nouveau ajoute un élément. Le nouvel élément doit apparaître dans les deux l’Explorateur FarmApp et dans la vue de grille de données approprié.  
  
     Vous devez être en mesure de modifier le nom de l’élément dans la vue de grille de données. Vous pouvez également le supprimer à partir de là.  
  
 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
  
### <a name="about-the-code-to-add-an-element"></a>À propos du code pour ajouter un élément  
 Pour les nouveaux boutons de l’élément, le code suivant de remplacement est légèrement plus simple.  
  
```csharp  
private void NewSheepButton_Click(object sender, EventArgs e)  
{  
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
  {  
    farm.Animals.Add(new Sheep(farm.Partition)); ;  
    t.Commit();  
  }  
}  
  
```  
  
 Toutefois, ce code ne définit pas un nom par défaut pour le nouvel élément. Il ne s’exécute pas toute fusion personnalisée que vous avez pouvez définir dans le **élément fusion Directives** la DSL, et il ne s’exécute pas de code personnalisé de fusion qui ont été défini.  
  
 Par conséquent, nous vous recommandons d’utiliser <xref:Microsoft.VisualStudio.Modeling.ElementOperations> pour créer de nouveaux éléments. Pour plus d’informations, consultez [personnalisation de création d’éléments et le déplacement des](../modeling/customizing-element-creation-and-movement.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)   
 [Écriture de Code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [SDK de modélisation pour Visual Studio - Langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)