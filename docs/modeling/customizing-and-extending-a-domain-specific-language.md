---
title: "Personnalisation et extension d’un langage spécifique au domaine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: 48
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 00a120fc470393f8ab843636ca5d3400b004232b
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Personnalisation et extension d'un langage spécifique à un domaine
Visual Studio de modélisation et de visualisation de kit de développement logiciel (SDK) VISUALIZATION fournit plusieurs niveaux à laquelle vous pouvez définir des outils de modélisation :  
  
1.  Définir un langage spécifique à un domaine (DSL) à l’aide du diagramme de définition DSL. Vous pouvez rapidement créer une solution DSL avec une notation visuelle, un formulaire XML lisible et les outils de base qui sont requises pour générer du code et autres artefacts.  
  
     Pour plus d’informations, consultez [comment définir un langage spécifique au domaine](../modeling/how-to-define-a-domain-specific-language.md).  
  
2.  Affinez la solution DSL à l’aide des fonctionnalités plus avancées de la définition DSL. Par exemple, vous pouvez afficher des liens supplémentaires lorsque l’utilisateur crée un élément. Ces techniques sont principalement obtenus dans la définition DSL et certaines nécessitent quelques lignes de code de programme.  
  
3.  Étendez vos outils de modélisation à l’aide du code de programme. Le Kit VMSDK a été conçu spécifiquement pour simplifier l'intégration à vos extensions avec le code généré à partir de la définition DSL.  Pour plus d’informations, consultez [écriture de Code pour personnaliser un langage spécifique au domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
> [!NOTE]
>  Lorsque vous avez mis à jour le fichier de définitions DSL, n’oubliez pas de cliquer sur **transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions avant de reconstruire votre solution.  
  
##  <a name="a-namecustomshapesa-in-this-section"></a><a name="customShapes"></a>Dans cette Section  
  
|Pour obtenir cet effet|Reportez-vous à cette rubrique|  
|----------------------------|-------------------------|  
|Autoriser l’utilisateur à définir les propriétés de couleur et le style de la forme.|Avec le bouton droit de la classe de forme ou le lien, pointez sur **ajouter exposées**, cliquez sur un élément.<br /><br /> Consultez la page [personnalisation de présentation sur le diagramme](../modeling/customizing-presentation-on-the-diagram.md).|  
|Différentes classes d’élément de modèle semblable dans le diagramme, partage des propriétés telles que la hauteur initiale et la largeur, couleur, les info-bulles.|Utiliser l’héritage entre les formes ou classes de connecteur. Les mappages entre les formes dérivées et les classes de domaine dérivées héritent les détails du mappage des parents.<br /><br /> Ou bien, mapper des classes de domaine différents pour la même classe de forme.|  
|Une classe d’élément de modèle est affichée par les contextes de différentes formes.|Mapper plusieurs classes de forme à la même classe de domaine. Lorsque vous générez la solution, suivez le rapport d’erreurs et fournir le code requis pour déterminer quelle forme à utiliser.|  
|Couleur de la forme ou autres fonctionnalités telles que les polices indiquent l’état actuel.|Consultez la page [mise à jour des formes et des connecteurs pour refléter le modèle](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Créer une règle qui met à jour les propriétés exposées. Consultez la page [règles propagent les modifications dans le modèle](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Sinon, utilisez OnAssociatedPropertyChanged() pour mettre à jour non exposé des fonctionnalités telles que les flèches de lien ou de la police.|  
|Icône sur change de forme pour indiquer l’état.|Définir la visibilité du mappage de décorateur dans la fenêtre Détails DSL. Recherchez plusieurs décorateurs d’image sur la même position. Consultez la page [mise à jour des formes et des connecteurs pour refléter le modèle](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Ou bien, remplacez `ImageField.GetDisplayImage()`. Consultez l’exemple dans <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.</xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>|  
|Définir une image d’arrière-plan sur n’importe quelle forme|Substituer InitializeInstanceResources() pour ajouter un ImageField ancré. Consultez la page [personnalisation de présentation sur le diagramme](../modeling/customizing-presentation-on-the-diagram.md).|  
|Imbriquer des formes à n’importe quelle profondeur|Permet de paramétrer une récursive incorporation d’arborescence. Définissez BoundsRules pour contenir les formes. Consultez la page [personnalisation de présentation sur le diagramme](../modeling/customizing-presentation-on-the-diagram.md).|  
|Reliez les connecteurs à des points fixes sur les limites d’un élément.|Définir les éléments terminal incorporées, représentées par petits ports sur le diagramme. Utilisez BoundsRules pour corriger les ports en place. Consultez l’exemple de diagramme de Circuit à [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128).|  
|Champ de texte affiche une valeur dérivée d’autres valeurs.|Mapper le décorateur de texte à une propriété de domaine calculée ou les stockage personnalisée. Pour plus d’informations, consultez [calculées et les propriétés de stockage personnalisé](../modeling/calculated-and-custom-storage-properties.md).|  
|Propager les modifications entre les éléments de modèle, ou entre les formes|Consultez la page [Validation dans un langage spécifique au domaine](../modeling/validation-in-a-domain-specific-language.md).|  
|Propager les modifications apportées aux ressources telles que les autres [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensions en dehors du magasin.|Consultez la page [gestionnaires d’événements propagent les modifications en dehors du modèle](../modeling/event-handlers-propagate-changes-outside-the-model.md).|  
|Fenêtre Propriétés affiche les propriétés d’un élément associé.|Configurer le transfert de propriété. Consultez la page [personnalisation de la fenêtre Propriétés](../modeling/customizing-the-properties-window.md).|  
|Catégories de propriétés|La fenêtre Propriétés est divisée en sections appelées catégories. Définir le **catégorie** de votre domaine. Propriétés portant le même nom de catégorie apparaissent dans la même section. Vous pouvez également définir le **catégorie** d’un rôle de relation.|  
|Contrôler l’accès aux propriétés du domaine|Définissez **est consultable** false pour empêcher une propriété de domaine dans la fenêtre Propriétés au moment de l’exécution. Vous pouvez toujours mapper au décorateurs de texte.<br /><br /> **Est l’interface utilisateur en lecture seule** empêche les utilisateurs de modifier une propriété de domaine.<br /><br /> Programme d’accéder à la propriété de domaine n’est pas affecté.|  
|Modifier le nom, icône et la visibilité des nœuds dans l’Explorateur de modèle de votre DSL.|Consultez la page [personnalisation de l’Explorateur de modèles](../modeling/customizing-the-model-explorer.md).|  
|Activer le copier, couper et coller|Définir le **activer copier coller** propriété de la **éditeur** nœud dans l’Explorateur DSL.|  
|Copier leurs objectifs et les liens de référence chaque fois qu’un élément est copié. Par exemple, copiez les commentaires joints à un élément.|Définir le **propage la copie** la propriété du rôle source (représenté par la ligne de chaque côté de la relation de domaine dans le schéma de définition DSL).<br /><br /> Écrire du code pour remplacer ProcessOnCopy pour obtenir des effets plus complexes.<br /><br /> Consultez la page [personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md).|  
|Supprimer, apparenter à nouveau ou relier des éléments connexes lorsqu’un élément est supprimé.|Définir le **propage supprimer** valeur d’un rôle de relation. Pour obtenir des effets plus complexes, remplacer `ShouldVisitRelationship` et `ShouldVisitRolePlayer` méthodes dans le `MyDslDeleteClosure` classe, défini dans **DomainModel.cs**<br /><br /> Consultez [personnalisation du comportement de suppression](../modeling/customizing-deletion-behavior.md)|  
|Conserver la mise en forme et l’apparence de copie et de glisser-déplacer.|Ajoutez les formes et connecteurs à copié `ElementGroupPrototype`. Est la méthode la plus pratique de remplacement`ElementOperations.CreateElementGroupPrototype()`<br /><br /> Consultez la page [personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md).|  
|Coller des formes à un emplacement choisi, par exemple la position actuelle du curseur.|Substituer `ClipboardCommandSet.ProcessOnCopy()` à utiliser la version spécifique à l’emplacement de `ElementOperations.Merge().` voir [personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md).|  
|Créer des liens supplémentaires lors du collage|Substituer ClipboardCommandSet.ProcessOnPasteCommand()|  
|Que le glisser-déposer des éléments à partir de ce diagramme, les autres fenêtres et DSL|Consultez [Comment : ajouter un gestionnaire glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|Autoriser une forme ou un outil pour les faire glisser vers une forme enfant, tel qu’un port, comme s’il était de faire glisser le parent.|Définir la Directive de fusion d’un élément sur la classe d’objet cible, pour transférer l’objet déplacé vers le parent. Consultez la page [personnalisation de création d’éléments et de déplacement des](../modeling/customizing-element-creation-and-movement.md).|  
|Autoriser une forme ou un outil permettant de faire glisser vers une forme et liens supplémentaires ou des objets créés. Par exemple, pour autoriser un commentaire à être déposé sur un élément auquel il doit être lié.|Définir une Directive de fusion d’élément sur la classe de domaine cible et définir les liens à générer. Dans les cas complexes, vous pouvez ajouter du code personnalisé. Consultez la page [personnalisation de création d’éléments et de déplacement des](../modeling/customizing-element-creation-and-movement.md).|  
|Créer un groupe d’éléments avec un seul outil. Par exemple, un composant avec un ensemble fixe de ports.|Remplacez la méthode d’initialisation de boîte à outils de ToolboxHelper.cs. Créer un Prototype de groupe élément (EGP) qui contient les éléments et leurs liens de relation. Consultez la page [personnalisation des outils et la boîte à outils](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Incluent les formes principal et le ports dans l’EGP, soit définir BoundsRules pour positionner les formes port lorsque l’EGP est instancié. Consultez la page [forme emplacement et taille de la classe BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md).|  
|Utilisez un outil de connexion pour instancier plusieurs types de relation.|Ajouter le lien se connecter Directives (LCD) au Générateur de connexion qui est appelé par l’outil. Les écrans LCD déterminent le type de la relation entre les types des deux éléments. Pour rendre cette opération varient selon les États des éléments, vous pouvez ajouter du code personnalisé. Consultez la page [personnalisation des outils et la boîte à outils](../modeling/customizing-tools-and-the-toolbox.md).|  
|Outils permanents : l’utilisateur peut double-cliquer sur n’importe quel outil pour créer de nombreuses formes ou des connecteurs à la suite.|Dans l’Explorateur DSL, sélectionnez le `Editor` nœud. Dans la fenêtre Propriétés, définissez **utilise des éléments de boîte à outils permanent**.|  
|Définir des commandes de menu|Consultez [Comment : modifier une commande de Menu Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|Restreindre le modèle avec des règles de validation|Consultez [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md)|  
|Générer le code, des fichiers de configuration ou des documents à partir d’une ligne DSL.|[Génération de code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Personnaliser la façon dont les modèles sont enregistrés au fichier.|Consultez [personnalisation du stockage de fichiers et la sérialisation XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Enregistrer les modèles dans les bases de données ou un autre support.|Substituer *Votre_langage*DocData<br /><br /> Consultez [personnalisation du stockage de fichiers et la sérialisation XML](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Intégrer plusieurs DSL afin qu’ils fonctionnent dans le cadre d’une application.|Consultez la page [intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|  
|Votre DSL à être étendue par des tiers et de contrôler l’extension.|[Étendre votre DSL à l’aide de MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Partage de classes entre plusieurs DSL à l’aide d’une bibliothèque DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Définition d’une stratégie de verrouillage pour créer des segments en lecture seule](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|  
|||  
  
## <a name="see-also"></a>Voir aussi  
 [Comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)   
 [Écrire du Code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [SDK de modélisation pour Visual Studio - Langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


