---
title: "Personnalisation des outils et la boîte à outils | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords: Domain-Specific Language, toolbox
ms.assetid: 2a0d03d7-ebc6-4458-b9f4-d2cb8418a62d
caps.latest.revision: "26"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: f7499aba9d7458ca1bf834bb168a25c6a6ae9b5c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="customizing-tools-and-the-toolbox"></a>Personnalisation des outils et de la boîte à outils
Vous devez définir les éléments de boîte à outils pour les éléments que les utilisateurs sont autorisés à ajouter à leurs modèles. Il existe deux types d'outils : les outils d'élément et les outils de connexion. Dans le concepteur généré, un utilisateur peut sélectionner un outil d'élément pour déplacer des formes vers le diagramme et sélectionner un outil de connexion pour tracer des liens entre les formes. En général, les outils d'élément permettent aux utilisateurs d'ajouter des instances de classes de domaine à leurs modèles et les outils de connexion d'ajouter des instances de relations de domaine.  
  
 Dans cette rubrique :  
  
-   [La définition de la boîte à outils](#ToolboxDef)  
  
-   [Personnalisation des outils d’élément](#customizing)  
  
-   [Création de groupes d’éléments à partir d’un outil](#groups)  
  
-   [Personnalisation des outils de connexion](#connections)  
  
##  <a name="ToolboxDef"></a>La définition de la boîte à outils  
 Dans l'Explorateur DSL, développez le nœud Éditeur et les nœuds sous-jacents. Généralement, vous voyez une arborescence qui se présente ainsi :  
  
```  
  
Editor  
     Toobox Tabs  
        MyDsl          //a tab  
           Tools  
               ExampleElement      // an element tool  
               ExampleRelationship // a connection tool  
  
```  
  
 Dans cette partie de l'Explorateur DSL, vous pouvez :  
  
-   Créer des onglets. Les onglets définissent les en-têtes de section de la boîte à outils.  
  
-   Créer des outils.  
  
-   Copier et coller des outils.  
  
-   Monter ou descendre des outils dans la liste.  
  
-   Supprimer des onglets et des outils.  
  
> [!IMPORTANT]
>  Pour ajouter ou coller des éléments dans un Explorateur DSL, cliquez avec le bouton droit sur le grand-parent du nouveau nœud. Par exemple, pour ajouter un outil, cliquez sur l’onglet et non le **outils** nœud. Pour ajouter un onglet, cliquez sur le **éditeur** nœud.  
  
 Le **icône Boîte à outils** propriété de chaque outil fait référence à un fichier bitmap 16 x 16. Ces fichiers sont généralement conservés dans le **Dsl\Resources** dossier.  
  
 Le **classe** propriété d’un outil d’élément fait référence à une classe concrète de domaine. Par défaut, l'outil crée les instances de cette classe. Cependant, vous pouvez écrire le code pour que l'outil crée des groupes d'éléments ou des éléments de différents types.  
  
 Le **connexion Générateur** propriété d’un outil de connexion fait référence à un générateur de connexion, qui définit les types d’éléments de l’outil peut se connecter, et quelles sont les relations crée entre eux. Les générateurs de connexions sont définis comme nœuds dans l'Explorateur DSL. Les générateurs de connexions sont créés automatiquement lorsque vous définissez les relations de domaine, mais vous pouvez écrire le code qui permet de les personnaliser.  
  
#### <a name="to-add-a-tool-to-the-toolbox"></a>Pour ajouter un outil à la boîte à outils  
  
1.  Vous créez généralement un outil d'élément après avoir créé une classe de formes et l'avoir mappée sur une classe de domaines.  
  
     Vous créez généralement un outil de connecteur après avoir créé une classe de connecteurs et l'avoir mappée sur une relation de référence.  
  
2.  Dans l’Explorateur DSL, développez le **éditeur** nœud et le **onglets de boîte à outils** nœud.  
  
     Cliquez sur un nœud d’onglet de boîte à outils, puis cliquez sur **ajouter un nouvel outil d’élément** ou **ajouter un nouvel outil de connexion**.  
  
3.  Définir le **icône Boîte à outils** propriété pour faire référence à une image bitmap 16 x 16.  
  
     Si vous souhaitez définir une nouvelle icône, créez un fichier bitmap dans l’Explorateur de solutions dans le **Dsl\Resources** dossier. Le fichier doit avoir des valeurs de propriété suivantes : **Action de génération** = **contenu**; **Copier dans le répertoire de sortie** = **ne copiez pas**.  
  
4.  **Pour un outil d’élément :** définir le **classe** propriété de l’outil pour faire référence à une classe concrète de domaine qui est mappée à une forme.  
  
     **Pour un outil de connecteur :** définir le **connexion Générateur** propriété de l’outil à un des éléments qui sont proposés dans la liste déroulante. Les générateurs de connexions sont automatiquement créés lorsque vous mappez un connecteur sur une relation de domaine. Si vous avez créé récemment un connecteur, vous devez normalement sélectionner le générateur de connexions associé.  
  
5.  Pour tester le DSL, appuyez sur F5 ou CTRL+F5, et dans l'instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ouvrez un exemple de fichier modèle. Le nouvel outil doit apparaître sur la boîte à outils. Faites-le glisser vers le diagramme pour vérifier qu'un nouvel élément a été créé.  
  
     Si l'outil n'apparaît pas, arrêtez l'instance expérimentale de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dans les fenêtres **Démarrer** menu, exécutez **réinitialiser l’Instance expérimentale de Microsoft Visual Studio 2010**. Sur le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **générer** menu, cliquez sur **régénérer la Solution**. Puis, testez à nouveau le DSL.  
  
##  <a name="customizing"></a>Personnalisation des outils de l’élément  
 Par défaut, l'outil crée une seule instance de la classe spécifiée, mais vous pouvez modifier ce comportement de deux façons :  
  
-   Définissez Directives de fusion d'éléments sur d'autres classes, en leur permettant d'accepter de nouvelles instances de cette classe et de créer des liens supplémentaires lorsque le nouvel élément est créé. Par exemple, vous pouvez autoriser l'utilisateur à déposer un Commentaire sur un autre élément et à créer ainsi un lien de référence entre les deux éléments.  
  
     Ces personnalisations affectent aussi ce qui se passe quand l'utilisateur colle ou fait glisser un élément.  
  
     Pour plus d’informations, consultez [personnalisation de création d’éléments et le déplacement des](../modeling/customizing-element-creation-and-movement.md).  
  
-   Écrivez le code pour personnaliser l'outil de telle sorte qu'il puisse créer des groupes d'éléments. L'outil est initialisé par des méthodes de ToolboxHelper.cs que vous pouvez remplacer. Pour plus d’informations, consultez [création de groupes d’éléments à partir d’un outil](#groups).  
  
##  <a name="groups"></a>Création de groupes d’éléments à partir d’un outil  
 Chaque outil d'élément contient un prototype des éléments qu'il doit créer. Par défaut, chaque outil d'élément crée un seul élément, mais il est également possible de créer un groupe d'objets liés avec un seul outil. Pour ce faire, vous initialisez l'outil avec un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> qui contient les éléments liés.  
  
 L'exemple suivant est extrait d'un DSL dans lequel se trouve un type Transistor. Chaque Transistor possède trois Terminaux nommés. L'outil d'élément pour Transistors stocke un prototype contenant quatre éléments de modèle et trois liens de relation. Lorsque l'utilisateur déplace l'outil sur le diagramme, le prototype est instancié et lié à la racine du modèle.  
  
 Ce code substitue une méthode qui est définie dans **Dsl\GeneratedCode\ToolboxHelper.cs**.  
  
 Pour plus d’informations sur la personnalisation du modèle à l’aide du code de programme, consultez [navigation et la mise à jour d’un modèle de Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
  public partial class CircuitsToolboxHelper  
  {  
    /// <summary>  
    /// Toolbox initialization, called for each element tool on the toolbox.  
    /// This version deals with each Component subtype separately.  
    /// </summary>  
    /// <param name="store"></param>  
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>  
    /// <returns>prototype of the object or group of objects to be created by tool</returns>  
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)  
    {  
        if (domainClassId == Transistor.DomainClassId)  
        {  
            Transistor transistor = new Transistor(store);  
  
            transistor.Base = new ComponentTerminal(store);  
            transistor.Collector = new ComponentTerminal(store);  
            transistor.Emitter = new ComponentTerminal(store);  
  
            transistor.Base.Name = "base";  
            transistor.Collector.Name = "collector";  
            transistor.Emitter.Name = "emitter";  
  
            // Create an ElementGroup for the Toolbox.  
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);  
            elementGroup.AddGraph(transistor, true);  
            // AddGraph includes the embedded parts  
  
            return elementGroup.CreatePrototype();  
        }  
        else  
        {  
            return base.CreateElementToolPrototype(store, domainClassId);  
}  }    }  
  
```  
  
##  <a name="connections"></a>Personnalisation des outils de connexion  
 Généralement, vous créez un outil d'élément lorsque vous créez une classe de connecteurs. Une autre solution consiste à surcharger un outil en autorisant les types des deux extrémités à déterminer le type de la relation. Par exemple, vous pouvez définir un outil de connexion capable de créer à la fois des relations de type Personne-Personne et des relations de type Personne-Ville.  
  
 Les outils de connexion invoquent les générateurs de connexions. Utilisez les générateurs de connexions pour spécifier de quelle façon les utilisateurs peuvent lier les éléments dans le concepteur généré. Les générateurs de connexions spécifient les éléments qui peuvent être liés et le type de lien créé entre eux.  
  
 Lorsque vous créez une relation de référence entre classes de domaine, un générateur de connexions est automatiquement créé. Vous pouvez utiliser ce générateur de connexions lors du mappage d'un outil de connexion. Pour plus d’informations sur la façon de créer des outils de connexion, consultez [configuration de la boîte à outils](../modeling/customizing-tools-and-the-toolbox.md).  
  
 Vous pouvez modifier le générateur de connexions par défaut de telle sorte qu'il puisse traiter un éventail différent de types source et cible, et créer différents types de relation.  
  
 Vous pouvez aussi écrire le code personnalisé des générateurs de connexions pour spécifier les classes source et cible de la collection, définir le type de connexion à établir et déclencher d'autres actions associées à la création d'une connexion.  
  
### <a name="the-structure-of-connection-builders"></a>Structure des générateurs de connexions  
 Les générateurs de connexions contiennent une ou plusieurs directives de connexion de liens, qui spécifient la relation de domaine et les éléments source et cible. Par exemple, dans le modèle de solution de flux de tâches, vous pouvez voir les **CommentReferencesSubjectsBuilder** dans les **Explorateur DSL**. Le Générateur de connexion contient un seul lien se connecter à la directive nommée **CommentReferencesSubjects**, qui est mappée à la relation de domaine **CommentReferencesSubjects**. Cette directive de connexion de liens contient une directive de rôle source qui pointe vers la classe de domaine `Comment` et une directive de rôle cible qui pointe vers la classe de domaine `FlowElement`.  
  
### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Utilisation de générateurs de connexion pour limiter les rôles source et cible  
 Vous pouvez utiliser les générateurs de connexion pour restreindre l'occurrence de certaines classes dans le rôle source ou le rôle cible d'une relation de domaine donnée. Par exemple, il se peut que vous ayez une classe de domaine de base avec une relation de domaine vers une autre classe de domaine, mais que vous ne vouliez pas que toutes les classes dérivées de la classe de base aient les mêmes rôles dans cette relation. Dans la solution de flux de tâches, il existe quatre classes concrètes domaine (**StartPoint**, **point de terminaison**, **MergeBranch**, et **synchronisation**) qui hérite directement de la classe abstraite domaine **élément FlowElement**, et deux concret des classes de domaine (**tâche** et **ObjectInState**) qui hériter indirectement. Il existe également un **flux** relation prend de référence **élément FlowElement** classes de domaine dans son rôle source et le rôle cible. Toutefois, une instance d’un **point de terminaison** classe de domaine ne doit pas être la source d’une instance d’un **flux** relation, ni doit une instance d’un **StartPoint** classe être le cible d’une instance d’un **flux** relation. Le **FlowBuilder** Générateur de connexion a un lien se connecter à la directive nommée **flux** qui spécifie quelles classes de domaine peuvent jouer le rôle de source (**tâche**,  **MergeBranch**, **StartPoint**, et **synchronisation**) et qui peuvent jouer le rôle de cible (**MergeBranch**,  **Point de terminaison**, et **synchronisation**).  
  
### <a name="connection-builders-with-multiple-link-connect-directives"></a>Générateurs de connexions avec plusieurs directives de connexion de liens  
 Vous pouvez ajouter plusieurs directives de connexion de liens à un générateur de connexions. Vous pouvez masquer une partie de la complexité du modèle de domaine à partir d’utilisateurs et de conserver le **boîte à outils** de surcharger trop. Vous pouvez ajouter les directives de connexion de liens de différentes relations de domaine à un seul générateur de connexions. Cependant, vous devez regrouper les relations de domaine quand elles exécutent à peu près la même fonction.  
  
 Dans la solution de flux de tâches, le **flux** outil de connexion est utilisé pour dessiner les instances des deux le **flux** et le **transition** des relations de domaine. Le **FlowBuilder** possède de générateur de connexion, en plus de la **flux** lien se connecter à la directive décrite précédemment, deux lien se connecter directives nommés **transition**. Ces directives spécifient qu’une instance d’un **transition** relation peut-être être établie entre des instances de la **ObjectInState** classe de domaine, ou à partir d’une instance d’un **ObjectInState**  à une instance d’un **tâche**, mais pas entre deux instances d’un **tâche**, ou à partir d’une instance d’un **tâche** à une instance d’un **ObjectInState**. Toutefois, une instance d’un **flux** relation peut être établie entre deux instances d’un **tâche**. Si vous compilez et exécutez la solution de flux de tâches, vous pouvez voir ce dessin un **flux** à partir d’une instance d’une **ObjectInState** à une instance d’un **tâche** crée une instance d’une **Transition**, mais dessin un **flux** entre deux instances d’un **tâche** crée une instance d’un **flux**.  
  
### <a name="custom-code-for-connection-builders"></a>Code personnalisé pour générateurs de connexions  
 Les quatre cases à cocher de l'interface utilisateur définissent différents types de personnalisation de générateurs de connexions :  
  
-   le **personnalisé accepter** case à cocher dans une directive de rôle source ou cible  
  
-   le **de connexion personnalisées** case à cocher dans une directive de rôle source ou cible  
  
-   le **utilise une connexion personnalisée** case à cocher dans une directive de se connecter  
  
-   le **personnalisé d’est** propriété du Générateur de connexion  
  
 Vous devez écrire un certain code de programme pour procéder à ces personnalisations. Pour savoir quel code vous devez fournir, cochez l'une de ces cases, cliquez sur Transformer tous les modèles, puis générez votre solution. Il en résultera un rapport d'erreurs. Double-cliquez sur le rapport d'erreurs pour afficher un commentaire expliquant quel code vous devez ajouter.  
  
> [!NOTE]
>  Pour ajouter un code personnalisé, créez une définition de classe partielle dans un fichier de code distinct des fichiers de code des dossiers GeneratedCode. Pour éviter de perdre votre travail, vous ne devez pas modifier les fichiers de code générés. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).  
  
#### <a name="creating-custom-connection-code"></a>Création du code de connexion personnalisé  
 Dans chaque lien de connexion directive, le **de Source de directives de rôle** onglet définit à partir de les types que vous pouvez faire glisser. De même, la **cibler des directives de rôle** onglet définit pour les types que vous pouvez faire glisser. Pour chaque type, vous pouvez plus spécifier s’il faut autoriser la connexion (pour la connexion à ce lien, la directive) en définissant le **personnalisé accepter** indicateur et puis en fournissant le code supplémentaire.  
  
 Vous pouvez également personnaliser ce qui se produit quand la connexion est établie. Par exemple, vous pouvez personnaliser uniquement le cas où le déplacement se produit vers ou depuis une classe particulière, tous les cas commandés par une directive de connexion de liens ou la totalité du générateur de connexions FlowBuilder. Pour chacune de ces options, vous pouvez définir des indicateurs personnalisés au niveau approprié. Lorsque vous transformez tous les modèles et essayez de générer la solution, les messages d'erreur vous dirigent vers les commentaires qui se trouvent dans le code généré. Ces commentaires identifient ce que vous devez fournir.  
  
 Dans l'exemple Diagramme de composants, le générateur de connexions de la relation de domaine Connexion est personnalisé pour limiter les connexions qui peuvent être établies entre les ports. L'illustration suivante montre que vous ne pouvez établir des connexions qu'à partir des éléments `OutPort` vers les éléments `InPort`, mais que vous pouvez imbriquer des composants les uns à l'intérieur des autres.  
  
 **Connexion arrivant à un OutPort à partir d’un composant imbriqué**  
  
 ![Générateur de connexion](../modeling/media/connectionbuilder_3.png "ConnectionBuilder_3")  
  
 Par conséquent, il se peut que vous vouliez spécifier qu'une connexion puisse aller d'un composant imbriqué vers un OutPort. Pour spécifier une telle connexion, vous définissez **accepter de personnalisé utilise** sur la **InPort** type en tant que rôle source et le **OutPort** type en tant que rôle de cible dans le **détails DSL**  fenêtre, comme indiqué dans les illustrations suivantes :  
  
 **Lien de se connecter à la Directive dans l’Explorateur de DSL**  
  
 ![Image du Générateur de connexion](../modeling/media/connectionbuilder_4a.png "ConnectionBuilder_4a")  
  
 **Lien de se connecter à la Directive dans la fenêtre des détails DSL**  
  
 ![](../modeling/media/connectionbuilder_4b.png "ConnectionBuilder_4b")  
  
 Vous devez ensuite fournir les méthodes de la classe ConnectionBuilder :  
  
```  
  public partial class ConnectionBuilder  
  {  
    /// <summary>  
    /// OK if this component has children  
    /// </summary>  
    private static bool CanAcceptInPortAsSource(InPort candidate)  
    {  
       return candidate.Component.Children.Count > 0;  
    }  
  
    /// <summary>  
    /// Only if source is on parent of target.  
    /// </summary>  
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)  
    {  
      return sourceInPort.Component == targetInPort.Component.Parent;  
    }  
// And similar for OutPorts...  
```  
  
 Pour plus d’informations sur la personnalisation du modèle à l’aide du code de programme, consultez [navigation et la mise à jour d’un modèle de Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Vous pouvez utiliser un code similaire pour empêcher, par exemple, les utilisateurs de créer des boucles avec des liens parent-enfant. Ces restrictions sont considérées comme des contraintes 'durs', car les utilisateurs ne peut pas violer les à tout moment. Vous pouvez également créer des contrôles de validation de 'l’option soft' utilisateurs pouvant contourner temporairement en créant des configurations non valides qu’ils ne peuvent pas enregistrer.  
  
### <a name="good-practice-in-defining-connection-builders"></a>Meilleure pratique de définition des générateurs de connexions  
 Vous devez définir un générateur de connexions pour créer différents types de relation uniquement s'ils sont conceptuellement associés. Dans l'exemple du flux de tâches, vous utilisez le même générateur pour créer des flux entre les tâches, ainsi qu'entre les tâches et les objets. Cependant, l'utilisation du même générateur pour créer des relations entre commentaires et tâches serait source de confusion.  
  
 Si vous définissez un générateur de connexions pour plusieurs types de relation, vous devez vous assurer qu'il ne puisse pas correspondre à plus d'un type de la même paire d'objets source et cible. Sinon, les résultats seront imprévisibles.  
  
 Code personnalisé vous permet d’appliquer des contraintes « durs », mais vous devez envisager si les utilisateurs doivent pouvoir modifier temporairement les connexions non valides. S'ils le peuvent, vous pouvez modifier les contraintes de telle sorte que les connexions ne soient pas validées tant que les utilisateurs n'ont pas enregistré les modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de la création d’élément et le déplacement](../modeling/customizing-element-creation-and-movement.md)   
 [Personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md)   
 [Comment : ajouter un gestionnaire de glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Navigation et la mise à jour d’un modèle de Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Exemple de diagrammes de circuit DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)