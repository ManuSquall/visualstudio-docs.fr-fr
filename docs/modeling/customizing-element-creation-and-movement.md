---
title: "Personnalisation de la cr&#233;ation et du mouvement des &#233;l&#233;ments | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.elementmergedirective"
helpviewer_keywords: 
  - "Domain-Specific Language, directives de fusion d’élément"
ms.assetid: cbd28f15-dfd7-46bd-ab79-5430e3ed83c8
caps.latest.revision: 36
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 36
---
# Personnalisation de la cr&#233;ation et du mouvement des &#233;l&#233;ments
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez autoriser un élément à faire glisser vers un autre, à partir de la boîte à outils ou dans un collage ou de l’opération de déplacement. Vous pouvez avoir les éléments déplacés liés aux éléments cibles, à l’aide de relations que vous spécifiez.  
  
 Une directive de fusion d’élément (EMD) Spécifie que se passe-t-il lorsqu’un élément de modèle est *fusionnées* dans un autre élément de modèle. Cela se produit lorsque :  
  
-   L’utilisateur fait glisser à partir de la boîte à outils vers le diagramme ou une forme.  
  
-   L’utilisateur crée un élément à l’aide d’un menu Ajouter dans l’Explorateur ou une forme de compartiment.  
  
-   L’utilisateur déplace un élément d’un couloir à un autre.  
  
-   L’utilisateur colle un élément.  
  
-   Votre code de programme appelle la directive de fusion d’élément.  
  
 Bien que les opérations de création peuvent sembler être différent pour les opérations de copie, elles fonctionnent en fait de la même façon. Lorsqu’un élément est ajouté, par exemple à partir de la boîte à outils, un prototype de celui-ci est répliqué. Le prototype est fusionné dans le modèle de la même manière que les éléments qui ont été copiés à partir d’une autre partie du modèle.  
  
 La responsabilité d’une directive EMD consiste à déterminer comment un objet ou un groupe d’objets doit être fusionné dans un emplacement particulier dans le modèle. En particulier, il détermine quelles sont les relations doivent être instanciées pour lier du groupe dans le modèle. Vous pouvez également le personnaliser pour définir les propriétés et à créer des objets supplémentaires.  
  
 ![DSL &#45 ; EMD &#95 ; Fusion](../modeling/media/dsl-emd_merge.png "DSL-EMD_Merge")  
Le rôle d’une Directive de fusion d’élément  
  
 Une directive EMD est générée automatiquement lorsque vous définissez une relation d’incorporation. Cette valeur par défaut EMD crée une instance de la relation lorsque les utilisateurs ajoutent de nouvelles instances enfant au parent. Vous pouvez modifier ces EMDs par défaut, par exemple en ajoutant du code personnalisé.  
  
 Vous pouvez également ajouter vos propres EMDs dans la définition DSL, permettant aux utilisateurs de faire glisser ou coller des combinaisons différentes de classes fusionnées et la réception.  
  
## <a name="defining-an-element-merge-directive"></a>Définition d’une Directive de fusion d’élément  
 Vous pouvez ajouter des directives de fusion d’élément pour les classes de domaine, les relations de domaine, formes, connecteurs et des diagrammes. Vous pouvez ajouter ou recherchez-les dans l’Explorateur DSL sous la classe de domaine de réception. La classe de récepteur est la classe de domaine de l’élément qui est déjà dans le modèle, et sur lequel l’élément nouveau ou copié est fusionnée.  
  
 ![DSL &#45 ; EMD &#95 ; détails](../modeling/media/dsl-emd_details.png "DSL-EMD_Details")  
  
 Le **l’indexation de la classe** est la classe de domaine d’éléments qui peuvent être fusionnés dans les membres de la classe réceptrice. Les instances des sous-classes de la classe de l’indexation seront également fusionnées par cette EMD, sauf si vous définissez **s’applique aux sous-classes** sur False.  
  
 Il existe deux types de directive de fusion :  
  
-   Un **processus de fusion** directive spécifie les relations par lequel le nouvel élément doit être lié dans l’arborescence.  
  
-   Un **avant la fusion** directive redirige le nouvel élément à un autre élément de réception, en général un parent.  
  
 Vous pouvez ajouter du code personnalisé aux directives de fusion :  
  
-   Définissez **acceptation personnalisée d’utilise** pour ajouter votre propre code pour déterminer si une instance particulière de l’élément d’indexation doit être fusionnée dans l’élément cible. Lorsque l’utilisateur fait glisser à partir de la boîte à outils, le pointeur « non valide » indique si votre code n’autorise pas la fusion.  
  
     Par exemple, vous pouvez autoriser la fusion uniquement lorsque l’élément cible est dans un état particulier.  
  
-   Définir **fusion personnalisée utilise** pour ajouter l’indicatif propre pour définir les modifications apportées au modèle lors de la fusion est effectuée.  
  
     Par exemple, vous pouvez définir des propriétés dans l’élément fusionné à l’aide des données à partir de son nouvel emplacement dans le modèle.  
  
> [!NOTE]
>  Si vous écrivez du code de fusion personnalisée, il affecte uniquement les fusions qui sont effectuées à l’aide de cette EMD. Autres EMDs que fusionner le même type d’objet, ou en l’absence d’autre code personnalisé qui crée ces objets sans utiliser le EMD, puis ils ne seront pas affectés par votre code personnalisé de fusion.  
>   
>  Si vous souhaitez vous assurer qu’un élément ou une nouvelle relation est toujours traitée par votre code personnalisé, vous pouvez définir un `AddRule` sur la relation d’incorporation et un `DeleteRule` sur la classe de domaine de l’élément. Pour plus d’informations, consultez [propager les modifications dans le modèle de règles](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="example-defining-an-emd-without-custom-code"></a>Exemple : Définition d’une directive EMD sans code personnalisé  
 L’exemple suivant permet aux utilisateurs de créer un élément et un connecteur en même temps en faisant glisser depuis la boîte à outils vers une forme existante. L’exemple ajoute une directive EMD à la définition DSL. Avant cette modification, les utilisateurs peuvent faire glisser outils vers le diagramme, mais pas sur les formes existantes.  
  
 Les utilisateurs peuvent également coller des éléments sur d’autres éléments.  
  
#### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Pour permettre aux utilisateurs de créer un élément et un connecteur en même temps  
  
1.  Créer un nouveau langage DSL à l’aide de la **langage Minimal** modèle de solution.  
  
     Lorsque vous exécutez ce DSL, il vous permet de créer des formes et des liens entre les formes. Vous ne pouvez pas faire glisser un nouveau **ExampleElement** forme à partir de la boîte à outils vers une forme existante.  
  
2.  Pour permettre aux utilisateurs de fusionner les éléments sur `ExampleElement` formes, créez un nouveau EMD dans la `ExampleElement` classe de domaine :  
  
    1.  Dans **Explorateur DSL**, développez **Classes de domaine**. Cliquez sur `ExampleElement` puis **Ajouter nouvel élément fusionner la Directive**.  
  
    2.  Assurez-vous que le **Détails DSL** fenêtre est ouverte, vous pouvez voir les détails de la nouvelle EMD. (Menu : **Afficher**, **autres fenêtres**, **Détails DSL**.)  
  
3.  Définir les **l’indexation classe** dans la fenêtre Détails DSL, pour définir la classe d’éléments qui peut être fusionné sur `ExampleElement` objets.  
  
     Dans cet exemple, sélectionnez `ExampleElements`, de sorte que l’utilisateur peut faire glisser les nouveaux éléments sur les éléments existants.  
  
     Notez que la classe indexation devient le nom de la EMD dans l’Explorateur DSL.  
  
4.  Sous **fusion de processus en créant des liens**, ajoutez deux chemins d’accès :  
  
    1.  Un chemin d’accès lie le nouvel élément de modèle parent. L’expression de chemin d’accès que vous devrez entrer parcourt à partir de l’élément existant, de la relation d’incorporation au modèle parent. Enfin, il spécifie le rôle dans le nouveau lien qui sera attribué le nouvel élément. Le chemin d’accès est la suivante :  
  
         `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`  
  
    2.  Le chemin d’accès lie le nouvel élément à l’élément existant. L’expression de chemin d’accès spécifie la relation de référence et le rôle auquel le nouvel élément sera attribué. Ce chemin d’accès est la suivante :  
  
         `ExampleElementReferencesTargets.Sources`  
  
     Vous pouvez utiliser l’outil de navigation de chemin d’accès pour créer chaque chemin d’accès :  
  
    1.  Sous **fusion de processus en créant des liens à des chemins d’accès**, cliquez sur **\< ajouter le chemin d’accès>**.  
  
    2.  Cliquez sur la flèche déroulante à droite de l’élément de liste. Une arborescence s’affiche.  
  
    3.  Développez les nœuds dans l’arborescence pour former le chemin d’accès que vous souhaitez spécifier.  
  
5.  Tester la solution DSL :  
  
    1.  Appuyez sur F5 pour régénérer et exécuter la solution.  
  
         La reconstruction prendra plus longtemps que d’habitude, car le code généré sera actualisé à partir de modèles de texte pour se conformer à la nouvelle définition DSL.  
  
    2.  Lorsque l’instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a démarré, ouvrez un fichier de modèle de votre DSL. Créer des éléments de l’exemple.  
  
    3.  Faites glisser le **élément exemple** outil sur une forme existante.  
  
         Une nouvelle forme apparaît et est liée à la forme avec un connecteur existante.  
  
    4.  Copier une forme existante. Sélectionnez une autre forme, puis collez.  
  
         Une copie de la première forme est créée.  Il possède un nouveau nom et elle est liée à la deuxième forme avec un connecteur.  
  
 Notez les points suivants à partir de cette procédure :  
  
-   En créant des Directives de fusion d’éléments, vous pouvez autoriser n’importe quelle classe d’accepter n’importe quel autre élément. Le EMD est créé dans la classe de domaine de réception et de la classe de domaine accepté est spécifiée dans le **Index, classe** champ.  
  
-   En définissant les chemins d’accès, vous pouvez spécifier quels liens doivent être utilisé pour connecter le nouvel élément au modèle existant.  
  
     Les liens que vous spécifiez doivent inclure une relation d’incorporation.  
  
-   Le EMD affecte à la fois création à partir de la boîte à outils et les opérations de collage.  
  
     Si vous écrivez du code personnalisé qui crée de nouveaux éléments, vous pouvez appeler explicitement la EMD à l’aide de la `ElementOperations.Merge` méthode. Cela permet de s’assurer que votre code lie les nouveaux éléments dans le modèle de la même façon que les autres opérations. Pour plus d’informations, consultez [Personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md).  
  
## <a name="example-adding-custom-accept-code-to-an-emd"></a>Exemple : Ajout de code acceptation personnalisée à une directive EMD  
 En ajoutant le code personnalisé à une directive EMD, vous pouvez définir le comportement de fusion plus complexe. Cet exemple simple empêche l’utilisateur d’ajouter un nombre fixe d’éléments vers le diagramme. L’exemple modifie la valeur par défaut EMD qui accompagne une relation d’incorporation.  
  
#### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Pour écrire un code personnalisé accepter pour limiter ce que l’utilisateur peut ajouter  
  
1.  Créez un DSL à l’aide de la **langage Minimal** modèle de solution. Ouvrez le diagramme de définition DSL.  
  
2.  Dans l’Explorateur DSL, développez **Classes de domaine**, `ExampleModel`, **Directives de fusion d’élément**. Sélectionnez la directive de fusion d’élément nommé `ExampleElement`.  
  
     Cette EMD contrôle comment l’utilisateur peut créer `ExampleElement` objets dans le modèle, par exemple en le faisant glisser à partir de la boîte à outils.  
  
3.  Dans la **Détails DSL** fenêtre, sélectionnez **acceptation utilise personnalisée**.  
  
4.  Régénérez la solution. Cela prendra plus longtemps que d’habitude, car le code généré sera actualisé à partir du modèle.  
  
     Une erreur de build sera signalée, semblable à : « Company.ElementMergeSample.ExampleElement ne contient pas de définition pour CanMergeExampleElement... »  
  
     Vous devez implémenter la méthode `CanMergeExampleElement`.  
  
5.  Créer un nouveau fichier de code dans la **Dsl** projet. Remplacez son contenu par le code suivant et remplacez l’espace de noms à l’espace de noms de votre projet.  
  
    ```c#  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace Company.ElementMergeSample // EDIT.  
    {  
      partial class ExampleModel  
      {  
        /// <summary>  
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.  
        /// This happens when the user pastes an ExampleElement  
        /// or drags from the toolbox.  
        /// Determines whether the merge is allowed.  
        /// </summary>  
        /// <param name="rootElement">The root element in the merging EGP.</param>  
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>  
        /// <returns>True if the merge is allowed</returns>  
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)  
        {  
          // Allow no more than 4 elements to be added:  
          return this.Elements.Count < 4;  
        }  
      }  
    }  
  
    ```  
  
     Cet exemple simple restreint le nombre d’éléments qui peuvent être fusionnés dans le modèle parent. Pour les conditions plus intéressantes, la méthode peut inspecter les propriétés des liens de l’objet de réception. Il peut également inspecter les propriétés des éléments de fusionnées, qui sont contenues dans un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Pour plus d’informations sur `ElementGroupPrototypes`, consultez [Personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md). Pour plus d’informations sur la façon d’écrire du code qui lit un modèle, consultez la page [navigation et mise à jour d’un modèle de Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
6.  Tester la solution DSL :  
  
    1.  Appuyez sur F5 pour régénérer la solution. Lorsque l’instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] s’affiche, ouvrez une instance de votre DSL.  
  
    2.  Créer de nouveaux éléments de plusieurs façons :  
  
        1.  Faites glisser le **élément exemple** outil vers le diagramme.  
  
        2.  Dans la **exemple l’Explorateur de modèles**, cliquez sur le nœud racine, puis **Ajouter un nouvel élément d’exemple**.  
  
        3.  Copiez et collez un élément sur le diagramme.  
  
    3.  Vérifiez que vous ne pouvez pas utiliser une des options suivantes pour ajouter plus de quatre éléments au modèle. Il s’agit, car ils utilisent tous la Directive de fusion d’élément.  
  
## <a name="example-adding-custom-merge-code-to-an-emd"></a>Exemple : Ajout de code personnalisé de fusion à une directive EMD  
 Dans le code de la fusion personnalisée, vous pouvez définir ce qui se passe lorsque l’utilisateur fait glisser un outil ou colle un élément sur un élément. Il existe deux façons de définir une fusion personnalisée :  
  
1.  Définissez **utilise une fusion personnalisée** et fournir le code requis. Votre code remplace le code généré de fusion. Utilisez cette option si vous souhaitez redéfinir complètement le descriptif de la fusion.  
  
2.  Remplacer le `MergeRelate` (méthode) et éventuellement le `MergeDisconnect` (méthode). Pour ce faire, vous devez définir le **génère une Double dérivée** propriété de la classe de domaine. Votre code peut appeler le code généré de fusion dans la classe de base. Utilisez cette option si vous souhaitez effectuer des opérations supplémentaires après que la fusion a été effectuée.  
  
 Ces approches n’affectent que les fusions qui sont effectuées à l’aide de cette EMD. Si vous souhaitez affecter tous les moyens dans lequel l’élément fusionné peut être créé, une alternative consiste à définir un `AddRule` sur la relation d’incorporation et un `DeleteRule` sur la classe de domaine fusionnée. Pour plus d’informations, consultez [propager les modifications dans le modèle de règles](../modeling/rules-propagate-changes-within-the-model.md).  
  
#### <a name="to-override-mergerelate"></a>Substituer MergeRelate  
  
1.  Dans la définition DSL, assurez-vous que vous avez défini le EMD auquel vous souhaitez ajouter du code. Si vous le souhaitez, vous pouvez ajouter des chemins d’accès et définir accepter du code personnalisé comme décrit dans les sections précédentes.  
  
2.  Dans le schéma DslDefinition, sélectionnez la classe réceptrice de la fusion. En général, c’est la classe à la fin de la source d’une relation d’incorporation.  
  
     Par exemple, dans un langage DSL généré à partir de la solution de langage Minimal, sélectionnez `ExampleModel`.  
  
3.  Dans la **propriétés** configurez **génère une Double dérivée** à **true**.  
  
4.  Régénérez la solution.  
  
5.  Inspecter le contenu de **Dsl\Generated Files\DomainClasses.cs**. Recherche de méthodes nommées `MergeRelate` et examinez leur contenu. Cela vous aidera à écrire vos propres versions.  
  
6.  Dans un nouveau fichier de code, écrivez une classe partielle pour la classe de récepteur et remplacer le `MergeRelate` (méthode). N’oubliez pas d’appeler la méthode de base. Exemple :  
  
    ```c#  
    partial class ExampleModel  
    {  
      /// <summary>  
      /// Called when the user drags or pastes an ExampleElement onto the diagram.  
      /// Sets the time of day as the name.  
      /// </summary>  
      /// <param name="sourceElement">Element to be added</param>  
      /// <param name="elementGroup">Elements to be merged</param>  
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)  
      {  
        // Connect the element according to the EMD:  
        base.MergeRelate(sourceElement, elementGroup);  
  
        // Custom actions:   
        ExampleElement mergingElement = sourceElement as ExampleElement;  
        if (mergingElement != null)  
        {  
          mergingElement.Name = DateTime.Now.ToLongTimeString();  
        }  
      }  
    }  
  
    ```  
  
#### <a name="to-write-custom-merge-code"></a>Pour écrire du code personnalisé de fusion  
  
1.  Dans **Dsl\Generated Code\DomainClasses.cs**, inspecter des méthodes nommées `MergeRelate`. Ces méthodes créent des liens entre un élément et le modèle existant.  
  
     Par ailleurs, inspectez les méthodes nommées `MergeDisconnect`. Ces méthodes dissocier un élément à partir du modèle lorsqu’il doit être supprimé.  
  
2.  Dans **Explorateur DSL**, sélectionnez ou créez la Directive de fusion d’élément que vous souhaitez personnaliser. Dans la **Détails DSL** configurez **utilise une fusion personnalisée**.  
  
     Lorsque vous définissez cette option, le **processus de fusion** et **avant la fusion** options sont ignorées. Votre code est utilisé à la place.  
  
3.  Régénérez la solution. Il prendra plus longtemps que d’habitude, car les fichiers de code généré seront actualisés à partir du modèle.  
  
     Messages d’erreur seront affiche. Double-cliquez sur les messages d’erreur pour afficher les instructions dans le code généré. Ces instructions vous demande de fournir deux méthodes, `MergeRelate`*YourDomainClass* et `MergeDisconnect`*YourDomainClass*  
  
4.  Écrire les méthodes dans une définition de classe partielle dans un fichier de code séparé. Les exemples que vous inspecté précédemment doivent proposer ce que vous avez besoin.  
  
 Code de fusion personnalisée n’affectera pas le code qui crée des objets et des relations directement et n’affecte pas les autres EMDs. Pour vous assurer que vos modifications supplémentaires sont implémentées, quelle que soit la façon dont l’élément est créé, envisagez d’écrire un `AddRule` et une `DeleteRule` à la place. Pour plus d’informations, consultez [propager les modifications dans le modèle de règles](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="redirecting-a-merge-operation"></a>Redirection d’une opération de fusion  
 Une directive de fusion directe redirige la cible d’une opération de fusion. En règle générale, la nouvelle cible est le parent d’incorporation de la cible initiale.  
  
 Par exemple, dans une solution DSL qui a été créée avec le modèle de diagramme de composant, les Ports sont incorporés dans les composants. Les ports sont affichés sous forme de petites formes sur le bord d’une forme de composant. L’utilisateur crée des ports en faisant glisser l’outil Port sur une forme de composant. Parfois, l’utilisateur a fait glisser l’outil Port un port existant, au lieu du composant, mais l’opération échoue. Il s’agit d’une simple erreur lorsqu’il existe plusieurs ports existants. Pour aider l’utilisateur afin d’éviter ce désagrément, vous pouvez autoriser les ports pour les faire glisser vers un port existant, mais que l’action redirigée vers le composant parent. L’opération fonctionne comme si l’élément cible ont été le composant.  
  
 Vous pouvez créer une directive de fusion vers l’avant dans la solution de modèle de composant. Si vous compilez et exécutez la solution d’origine, vous devez voir que les utilisateurs peuvent faire glisser n’importe quel nombre de **Port d’entrée** ou **Port de sortie** éléments à partir de la **boîte à outils** à un **composant** élément. Toutefois, ils ne peuvent pas faire glisser un port à un port existant. Le pointeur indisponible les alertes que ce déplacement n’est pas activé. Toutefois, vous pouvez créer une directive de fusion vers l’avant afin qu’un port qui est accidentellement supprimé une **Port d’entrée** est transféré vers le **composant** élément.  
  
#### <a name="to-create-a-forward-merge-directive"></a>Pour créer une directive de fusion vers l’avant  
  
1.  Créer un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solution à l’aide du modèle de modèle de composant.  
  
2.  Afficher la **Explorateur DSL** en ouvrant DslDefinition.dsl.  
  
3.  Dans la **Explorateur DSL**, développez **Classes de domaine**.  
  
4.  Le **ComponentPort** classe de domaine abstraite est la classe de base des deux **InPort** et **OutPort**. Avec le bouton droit **ComponentPort** puis **Ajouter nouvel élément fusionner la Directive**.  
  
     Un nouveau **Directive de fusion d’élément** nœud apparaît sous la **Directives de fusion d’éléments** nœud.  
  
5.  Sélectionnez le **Directive de fusion d’élément** nœud et ouvrez le **Détails DSL** fenêtre.  
  
6.  Dans la liste des classes d’indexation sélectionnez **ComponentPort**.  
  
7.  Sélectionnez **transférer de fusion pour une classe de domaine différents**.  
  
8.  Dans la liste de sélection du chemin d’accès, développez **ComponentPort**, développez **ComponentHasPorts**, puis sélectionnez **composant**.  
  
     Le nouveau chemin d’accès doit ressembler à celle-ci :  
  
     **ComponentHasPorts.Component/!Component**  
  
9. Enregistrez la solution et transformer les modèles en cliquant sur le bouton plus à droite dans le **l’Explorateur de solutions** barre d’outils.  
  
10. Générez et exécutez la solution. Une nouvelle instance de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] s’affiche.  
  
11. Dans **l’Explorateur de solutions**, ouvrez Sample.mydsl. Le diagramme et le **boîte à outils ComponentLanguage** s’affichent.  
  
12. Faites glisser une **Port d’entrée** à partir de la **boîte à outils** à un autre **Port d’entrée.** Ensuite, faites glisser une **OutputPort** à une **InputPort** et ensuite à un autre **OutputPort**.  
  
     Vous ne devez pas voir le pointeur non disponible, et vous devez être en mesure de supprimer la nouvelle **Port d’entrée** sur celui-ci. Sélectionnez la nouvelle **Port d’entrée** et faites-le glisser vers un autre point la **composant**.  
  
## <a name="see-also"></a>Voir aussi  
 [Navigation et mise à jour d’un modèle de Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Personnalisation des outils et la boîte à outils](../modeling/customizing-tools-and-the-toolbox.md)   
 [Exemple de diagrammes de circuit DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)