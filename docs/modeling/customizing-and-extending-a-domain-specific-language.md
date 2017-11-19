---
title: "Personnalisation et l’extension d’un langage spécifique à un domaine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: "48"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: efdd7f5358ce0ec4afd32ebaa8ff1fd8d117dc47
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Personnalisation et extension d'un langage spécifique à un domaine
Visual Studio de modélisation et de visualisation SDK (VMSDK) fournit plusieurs niveaux à laquelle vous pouvez définir des outils de modélisation :  
  
1.  Définir un langage spécifique à un domaine (DSL) à l’aide du schéma de définition DSL. Vous pouvez rapidement créer DSL avec une notation sous forme de schéma, un format XML lisible et les outils de base qui sont requises pour générer le code et autres artefacts.  
  
     Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md).  
  
2.  Ajuster la DSL à l’aide des fonctionnalités plus avancées de la définition DSL. Par exemple, vous pouvez afficher des liens supplémentaires lorsque l’utilisateur crée un élément. Ces techniques sont principalement effectuées dans la définition DSL, et que certains requièrent peu de lignes de code de programme.  
  
3.  Étendre vos outils de modélisation à l’aide du code de programme. Le Kit VMSDK a été conçu spécifiquement pour simplifier l'intégration à vos extensions avec le code généré à partir de la définition DSL.  Pour plus d’informations, consultez [écriture de Code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
> [!NOTE]
>  Lorsque vous avez mis à jour le fichier de définitions de DSL, n’oubliez pas de cliquer sur **transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions, puis recommencez votre solution.  
  
##  <a name="customShapes"></a>Dans cette Section  
  
|Pour obtenir cet effet|Reportez-vous à cette rubrique|  
|----------------------------|-------------------------|  
|Autoriser l’utilisateur définir les propriétés de couleur et le style de la forme.|Avec le bouton droit de la classe de forme ou le lien, pointez sur **ajouter exposées**, cliquez sur un élément.<br /><br /> Consultez [personnalisation de présentation sur le diagramme](../modeling/customizing-presentation-on-the-diagram.md).|  
|Différentes classes d’élément de modèle semblable dans le diagramme, le partage des propriétés telles que la hauteur initiale et la largeur, couleur, les info-bulles.|Utilisez l’héritage entre les formes ou des classes de connecteur. Mappages entre les formes dérivées et les classes de domaine dérivée héritent les détails de mappage des parents.<br /><br /> Ou bien, mapper les classes de domaine différent à la même classe de forme.|  
|Une classe d’élément de modèle est affichée dans les contextes de différentes formes.|Mapper plusieurs classes de forme à la même classe de domaine. Lorsque vous générez la solution, suivez le rapport d’erreurs et fournissez le code requis pour déterminer quel forme à utiliser.|  
|Couleur de forme ou d’autres fonctionnalités telles que la police indiquent l’état actuel.|Consultez [mise à jour des formes et connecteurs pour refléter le modèle](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Créer une règle qui met à jour les propriétés exposées. Consultez [règles propagent les modifications dans le modèle](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Sinon, utilisez OnAssociatedPropertyChanged() pour mettre à jour non exposés à des fonctionnalités telles que les flèches de lien ou de la police.|  
|Icône sur change de forme pour indiquer l’état.|Définir la visibilité de l’élément décoratif mappage dans la fenêtre Détails DSL. Recherchez plusieurs décorateurs image sur la même position. Consultez [mise à jour des formes et connecteurs pour refléter le modèle](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Ou substituer `ImageField.GetDisplayImage()`. Consultez l’exemple dans <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.|  
|Définir une image d’arrière-plan sur n’importe quelle forme|Substituer InitializeInstanceResources() pour ajouter un ImageField ancré. Consultez [personnalisation de présentation sur le diagramme](../modeling/customizing-presentation-on-the-diagram.md).|  
|Imbriquer des formes à n’importe quelle profondeur|Configurer une récursive incorporation d’arborescence. Définissez BoundsRules pour contenir les formes. Consultez [personnalisation de présentation sur le diagramme](../modeling/customizing-presentation-on-the-diagram.md).|  
|Reliez les connecteurs à des points fixes sur les limites d’un élément.|Définir les éléments incorporés Terminal Server, représentées par petits ports sur le diagramme. BoundsRules permet de corriger les ports en place. Consultez l’exemple de diagramme de Circuit [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128).|  
|Champ de texte affiche une valeur dérivée d’autres valeurs.|Mapper la décoration de texte à une propriété de domaine calculé ou stockage de personnalisée. Pour plus d’informations, consultez [calculé et les propriétés de stockage personnalisé](../modeling/calculated-and-custom-storage-properties.md).|  
|Propager les modifications entre les éléments de modèle, ou entre les formes|Consultez [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md).|  
|Propager les modifications apportées aux ressources telles que les autres [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensions en dehors de la banque.|Consultez [gestionnaires d’événements propagent les modifications en dehors du modèle](../modeling/event-handlers-propagate-changes-outside-the-model.md).|  
|Fenêtre Propriétés affiche les propriétés d’un élément connexe.|Configurer le transfert de propriété. Consultez [personnalisation de la fenêtre Propriétés](../modeling/customizing-the-properties-window.md).|  
|Catégories de propriétés|La fenêtre Propriétés est divisée en sections appelés catégories. Définir le **catégorie** de votre domaine. Propriétés portant le même nom de catégorie apparaîtront dans la même section. Vous pouvez également définir le **catégorie** d’un rôle de relation.|  
|Contrôler l’accès aux propriétés du domaine|Définissez **est consultable** false pour empêcher une propriété de domaine dans la fenêtre Propriétés au moment de l’exécution. Vous pouvez toujours le mapper à des éléments décoratifs de texte.<br /><br /> **Est l’interface utilisateur en lecture seule** empêche les utilisateurs de modifier une propriété de domaine.<br /><br /> Programme d’accéder à la propriété de domaine n’est pas affectée.|  
|Modifier le nom, une icône et une visibilité de nœuds dans l’Explorateur de modèles de votre DSL.|Consultez [personnalisation de l’Explorateur de modèles](../modeling/customizing-the-model-explorer.md).|  
|Activer le copier, couper et coller|Définir le **activer copier, coller** propriété de la **éditeur** nœud dans l’Explorateur DSL.|  
|Copier les liens de référence et leurs cibles chaque fois qu’un élément est copié. Par exemple, copiez les commentaires joints à un élément.|Définir le **propage la copie** la propriété du rôle source (représenté par la ligne au côté « un » de la relation de domaine dans le schéma de définition DSL).<br /><br /> Écrire du code pour remplacer ProcessOnCopy pour obtenir des effets plus complexes.<br /><br /> Consultez [personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md).|  
|Supprimer, redéfinir la parenté ou rétablir les liens éléments connexes lorsqu’un élément est supprimé.|Définir le **propage supprimer** valeur d’un rôle de relation. Pour obtenir des effets plus complexes, substituez `ShouldVisitRelationship` et `ShouldVisitRolePlayer` méthodes dans le `MyDslDeleteClosure` (classe), défini dans **DomainModel.cs**<br /><br /> Consultez [personnaliser le comportement de suppression](../modeling/customizing-deletion-behavior.md)|  
|Conserver la disposition de forme et l’apparence de copie et de glisser-déplacer.|Ajouter les formes et connecteurs à copié `ElementGroupPrototype`. La méthode la plus commode de substitution est`ElementOperations.CreateElementGroupPrototype()`<br /><br /> Consultez [personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md).|  
|Coller des formes à un emplacement choisi, par exemple la position actuelle du curseur.|Substituer `ClipboardCommandSet.ProcessOnCopy()` à utiliser la version spécifique à l’emplacement de `ElementOperations.Merge().` consultez [personnalisation de comportement de copie](../modeling/customizing-copy-behavior.md).|  
|Créer des liens supplémentaires lors du collage|Substituer ClipboardCommandSet.ProcessOnPasteCommand()|  
|Activer faites glisser et déposez les éléments de ce diagramme et d’autres DSL et Windows|Consultez [Comment : ajouter un gestionnaire de glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|Autoriser une forme ou un outil pour les faire glisser vers une forme enfant, par exemple un port, comme s’il a été déplacé vers le parent.|Définir une Directive d’élément de fusion sur la classe d’objet cible, pour transférer l’objet déplacé vers le parent. Consultez [personnalisation de la création d’élément et le déplacement des](../modeling/customizing-element-creation-and-movement.md).|  
|Autoriser une forme ou un outil permettant de faire glisser vers une forme et ont des liens supplémentaires ou des objets créés. Par exemple, pour autoriser un commentaire à être déposé sur un élément auquel il doit être lié.|Définir une Directive d’élément de fusion sur la classe de domaine cible et définir les liaisons à générer. Dans les cas complexes, vous pouvez ajouter le code personnalisé. Consultez [personnalisation de la création d’élément et le déplacement des](../modeling/customizing-element-creation-and-movement.md).|  
|Créer un groupe d’éléments avec un seul outil. Par exemple, un composant avec un ensemble fixe de ports.|Substituez la méthode d’initialisation de boîte à outils dans ToolboxHelper.cs. Créer un élément de groupe de Prototype (EGP) contenant les éléments et leurs liens de relation. Consultez [personnalisation des outils et la boîte à outils](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Inclure les formes principales et le ports dans le EGP, ou définir BoundsRules afin de positionner les formes port lorsque le EGP est instancié. Consultez [forme emplacement et taille de la classe BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md).|  
|Utilisez un outil de connexion pour instancier plusieurs types de relation.|Ajouter le lien se connecter Directives (écran) pour le Générateur de connexion qui est appelé par l’outil. Les LCD déterminent le type de la relation à partir des types des deux éléments. Pour rendre cette varient selon les États des éléments, vous pouvez ajouter du code personnalisé. Consultez [personnalisation des outils et la boîte à outils](../modeling/customizing-tools-and-the-toolbox.md).|  
|Outils rémanentes - l’utilisateur pouvez double-cliquer sur n’importe quel outil pour créer de nombreuses formes ou des connecteurs à la suite.|Dans l’Explorateur DSL, sélectionnez le `Editor` nœud. Dans la fenêtre Propriétés, définissez **utilise des éléments de boîte à outils rémanentes**.|  
|Définir des commandes de menu|Consultez [Comment : modifier une commande de Menu Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|Contraignent le modèle avec les règles de validation|Consultez [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md)|  
|Générer le code, des fichiers de configuration ou des documents à partir de la DSL.|[Génération de code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Personnaliser la façon dont les modèles sont enregistrés au fichier.|Consultez [personnalisation de stockage de fichiers et la sérialisation XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Enregistrer les modèles dans les bases de données ou un autre support.|Substituer *YourLanguage*DocData<br /><br /> Consultez [personnalisation de stockage de fichiers et la sérialisation XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Intégrer plusieurs DSL afin qu’ils fonctionnent dans le cadre d’une application.|Consultez [intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|  
|Autoriser votre DSL à être étendue par des tiers et l’extension de contrôle.|[Étendre votre DSL à l’aide de MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Partage de classes entre plusieurs DSL à l’aide d’une bibliothèque DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Définition d’une stratégie de verrouillage pour créer des segments en lecture seule](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|
  
## <a name="see-also"></a>Voir aussi  
 [Comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)   
 [Écriture de Code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [SDK de modélisation pour Visual Studio - Langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

