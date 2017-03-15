---
title: "Fonctionnement des modèles, des Classes et des relations | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, models
ms.assetid: 2ecd569c-b369-41ea-b78e-a61b62e2e4e9
caps.latest.revision: 35
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: 4982dcc5c6fb0184f1f467971b6255aace6bec53
ms.lasthandoff: 02/22/2017

---
# <a name="understanding-models-classes-and-relationships"></a>Présentation des modèles, des classes et des relations
Un langage spécifique à un domaine (DSL) est défini par son fichier de définition DSL, ainsi que tout code de programme personnalisé que vous pouvez écrire. La plupart du code du programme dans la solution DSL est généré à partir de ce fichier.  
  
 Cette rubrique explique les fonctionnalités centrales de la définition DSL.  
  
## <a name="the-dsl-definition"></a>La définition DSL  
 Lorsque vous ouvrez `Dsl\DslDefinition.dsl`, votre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fenêtre ressemble à l’image suivante.  
  
 ![concepteur DSL](../modeling/media/dsl_designer.png "dsl_designer")  
  
 Les informations les plus importantes dans la définition DSL s’affiche dans le diagramme de définition DSL. Informations supplémentaires, qui fait également partie de DslDefinition.dsl, s’affiche dans l’Explorateur DSL, qui apparaît généralement sur le côté du diagramme. Vous travaillez avec le schéma pour les tâches les plus fréquentes et avec l’Explorateur DSL pour les personnalisations plus avancées.  
  
 Diagramme de définition DSL montre les classes de domaine qui définissent des éléments de modèle et les relations qui définissent des liens entre éléments de modèle. Il montre également les formes et connecteurs sont utilisés pour afficher les éléments de modèle à l’utilisateur.  
  
 ![concepteur DSL avec couloir](../modeling/media/dsl_desinger.png "dsl_desinger")  
  
 Lorsque vous sélectionnez un élément dans la définition DSL, sur le diagramme ou dans l’Explorateur DSL, des informations s’affiche dans la fenêtre Propriétés. Informations supplémentaires peuvent être affichées dans la fenêtre Détails DSL.  
  
### <a name="models-are-instances-of-dsls"></a>Les modèles sont des instances de DSL  
 A *modèle* est une instance de votre DSL créé par un utilisateur. Un modèle contient des éléments de modèle, qui sont des instances des classes de domaine que vous définissez et des liens entre les éléments qui sont des instances des relations de domaine que vous définissez. Un modèle peut être également les formes et connecteurs, qui affichent les éléments de modèle et les liens dans un diagramme. La définition DSL inclut les classes de forme et une classe pour le diagramme de classes de connecteur.  
  
 Une définition DSL est également appelé un *modèle de domaine*. Un modèle de définition DSL ou de domaine est la représentation sous forme de conception du langage spécifique à un domaine, alors que le modèle est l’instanciation d’exécution du langage spécifique à un domaine.  
  
## <a name="domain-classes-define-model-elements"></a>Classes de domaine définissent des éléments de modèle  
 Classes de domaine sont utilisés pour créer les divers éléments dans le domaine et les relations de domaine sont les liens entre les éléments. Ils sont la représentation au moment du design des éléments et des liens qui seront instanciés par les utilisateurs du langage spécifique à la conception lorsqu’ils créent leurs modèles.  
  
 Cette illustration montre un modèle qui a été créé par l’utilisateur d’une bibliothèque musicale DSL. Albums de musique sont représentées par des zones qui contiennent des listes de morceaux de musique. Artistes sont représentées par des zones aux angles arrondis et sont connectés aux albums sur lesquels ils ont contribué.  
  
 ![Modèle d’instance du DSL généré](../modeling/media/music_instance.png "Music_Instance")  
  
 La définition DSL sépare deux aspects. L’apparence des éléments du modèle sur le diagramme de modèle est défini à l’aide des classes de formes et des classes de connecteur. Les informations contenues dans le modèle sont définies à l’aide de classes de domaine et les relations de domaine.  
  
 L’illustration suivante montre les classes de domaine et les relations dans la définition DSL de la médiathèque.  
  
 ![Relations d’incorporation et de référence](../modeling/media/music_classes.png "Music_Classes")  
  
 L’illustration montre quatre classes de domaine : musique, Album, artiste et chanson. Les classes de domaine définissent des propriétés de domaine comme nom, titre et ainsi de suite. Dans le modèle d’instance, les valeurs de certaines de ces propriétés sont affichées dans le diagramme.  
  
 Entre les classes sont des relations de domaine : MusicHasAlbums, MusicHasArtists, AlbumbHasSongs et ArtistAppearedOnAlbums. Les relations ont les multiplicités tels que 1..1, 0.. *. Par exemple, chaque morceau de musique doit être associé à un seul Album via la relation AlbumHasSongs. Chaque Album peut avoir autant de morceaux de musique.  
  
### <a name="rearranging-the-dsl-definition-diagram"></a>Réorganiser le diagramme de définition DSL  
 Notez qu’une classe de domaine peut apparaître plusieurs fois sur le diagramme de définition DSL, contrairement à Album dans cette image. Il y a toujours une vue principale, et il peut y avoir certains *référence* vues.  
  
 Pour réorganiser le diagramme de définition DSL, vous pouvez :  
  
-   Échange principal et de référence aux vues à l’aide de la **déplacer l’arborescence ici** et **arborescence fractionnée** commandes. Cliquez sur une classe de domaine unique pour afficher ces commandes.  
  
-   Réorganiser les classes de domaine et les classes de formes en appuyant sur Ctrl + haut et Ctrl + bas.  
  
-   Réduire ou développer des classes à l’aide de l’icône dans l’angle supérieur droit de chaque forme.  
  
-   Réduire les parties de l’arborescence en cliquant sur le signe moins (-) en bas d’une classe de domaine.  
  
## <a name="inheritance"></a>Héritage  
 Classes de domaine peuvent être définies à l’aide de l’héritage. Pour créer une dérivation d’héritage, cliquez sur l’outil d’héritage, cliquez sur la classe dérivée, puis cliquez sur la classe de base. Un élément de modèle possède toutes les propriétés qui sont définies sur sa propre classe de domaine, ainsi que toutes les propriétés héritées de la classe de base. Il hérite également ses rôles dans les relations.  
  
 L’héritage peut également servir entre les relations, formes et connecteurs. L’héritage doit conserver dans le même groupe. Une forme ne peut pas hériter d’une classe de domaine.  
  
## <a name="domain-relationships"></a>Relations de domaine  
 Éléments de modèle peuvent être liés par des relations. Les liens sont toujours binaires ; ils renvoient exactement deux éléments. Toutefois, tout élément peut avoir de nombreux liens vers d’autres objets, et il peut même être plus d’un lien entre la même paire d’éléments.  
  
 Comme vous pouvez définir différentes classes d’éléments, vous pouvez définir des classes différentes de liens. La classe d’un lien est appelée un *relation de domaine*. Une relation de domaine spécifie les classes d’élément de ses instances peuvent se connecter. Chaque terminaison d’une relation est appelée une *rôle*, et la relation de domaine définit les noms pour les deux rôles, ainsi que pour la relation proprement dite.  
  
 Il existe deux types de relations de domaine : incorporation de relations et référence. Sur le diagramme de définition DSL, relations d’incorporation ont des lignes pleines à chaque rôle et les relations de référence ont des traits en pointillés.  
  
### <a name="embedding-relationships"></a>Relations d’incorporation  
 Chaque élément dans un modèle, à l’exception de la racine, est la cible d’une liaison d’incorporation. Par conséquent, l’ensemble du modèle forme une arborescence unique d’incorporation des liens. Une relation d’incorporation représente la relation contenant-contenu ou la propriété. Deux éléments de modèle qui sont liées de cette façon sont également appelés parent et enfant. L’enfant est dit être incorporé dans le parent.  
  
 Incorporation des liens généralement ne figurent pas explicitement en tant que liens dans un diagramme. Au lieu de cela, ils sont généralement représentés par le contenant. La racine du modèle est représentée par le diagramme et les éléments incorporés sont affichés en tant que formes sur le diagramme.  
  
 Dans l’exemple, la classe racine Music a une relation d’incorporation MusicHasAlbums album, ce qui a une incorporation AlbumHasSongs chanson. Morceaux est affichés sous forme d’éléments dans une liste à l’intérieur de chaque Album. Musique a également une incorporation MusicHasArtists à la classe artiste, dont les instances apparaissent également en tant que formes sur le diagramme.  
  
 Par défaut, les éléments incorporés sont automatiquement supprimés lorsque leurs parents sont supprimés.  
  
 Lorsqu’un modèle est enregistré pour le fichier au format XML, les éléments incorporés sont imbriqués dans leurs parents, sauf si vous avez personnalisé la sérialisation.  
  
> [!NOTE]
>  L'incorporation n'est pas la même chose que l'héritage. Les enfants dans une relation d’incorporation n’héritent pas les propriétés du parent. Une incorporation est un type de lien entre les éléments de modèle. L’héritage est une relation entre les classes et ne crée pas de liens entre les éléments de modèle.  
  
### <a name="embedding-rules"></a>Incorporation de règles  
 Chaque élément dans un modèle d’instance doit être la cible d’un seul lien incorporation, à l’exception de la racine du modèle.  
  
 Par conséquent, chaque classe non abstraite domaine, à l’exception de la classe racine, doit être la cible d’au moins une relation d’incorporation ou elle doit hériter d’une intégration à partir d’une classe de base. Une classe peut être la cible des incorporations de deux ou plus, mais ses éléments de modèle d’instance ne peuvent avoir qu’un seul parent à une heure. La multiplicité de la cible vers source doit être la valeur 0.. 1 ou 1.. 1.  
  
### <a name="the-explorer-displays-the-embedding-tree"></a>L’Explorateur affiche l’arborescence d’incorporation  
 Votre définition DSL crée également un Explorateur, les utilisateurs voient en même temps que leur schéma de modèle.  
  
 ![Explorateur généré de DSL](../modeling/media/music_explorer.png "Music_Explorer")  
  
 L’Explorateur affiche tous les éléments dans le modèle, même ceux pour lesquels vous n’avez pas défini de toutes les formes. Il affiche les éléments et les relations d’incorporation, mais pas les relations de référence.  
  
 Pour afficher les valeurs des propriétés d’un élément de domaine, l’utilisateur sélectionne un élément dans le diagramme ou dans l’Explorateur de modèles et la fenêtre Propriétés. Il affiche toutes les propriétés de domaine, y compris ceux qui ne sont pas affichés sur le diagramme. Dans l’exemple, chaque chanson a un titre et un Genre, mais uniquement la valeur du titre est affichée sur le diagramme.  
  
## <a name="reference-relationships"></a>Relations de référence  
 Une relation de référence représente n’importe quel type de relation qui n’est pas l’incorporation.  
  
 Relations de référence sont généralement affichées sur un diagramme sous forme de connecteurs entre les formes.  
  
 Dans la représentation XML du modèle, un lien de référence entre deux éléments est représenté à l’aide de *monikers.* Autrement dit, les monikers sont des noms qui identifient de façon unique chaque élément dans le modèle. Le nœud XML pour chaque élément de modèle contient un nœud qui spécifie le nom de la relation et le nom de l’autre élément.  
  
## <a name="roles"></a>Rôles  
 Chaque relation de domaine a deux rôles, un rôle de la source et un rôle cible.  
  
 Dans l’illustration suivante, la ligne entre les **Publisher** classe de domaine et le **PublisherCatalog** relation de domaine est le rôle de la source. La ligne de la relation de domaine et le **Album** classe de domaine est le rôle cible.  
  
 ![Rôles et propriétés. ] (../modeling/media/propertycode.png "PropertyCode")  
  
 Les noms associés à une relation sont particulièrement importants lorsque vous écrivez du code de programme qui traverse le modèle. Par exemple, lorsque vous générez la solution DSL, la classe générée Publisher a une propriété de catalogue qui est une collection d’Albums. La classe Album a une propriété de publication qui est une instance unique de la classe de serveur de publication.  
  
 Lorsque vous créez une relation dans une définition DSL, les noms de propriété et de relation reçoivent des valeurs par défaut. Toutefois, vous pouvez les modifier.  
  
## <a name="multiplicities"></a>Multiplicités  
 Multiplicités spécifient le nombre d’éléments peut avoir le même rôle dans une relation de domaine. Dans l’exemple, le zéro-à-plusieurs (0..\*) paramètre multiplicité sur le **catalogue** rôle spécifie que toutes les instances de la **Publisher** classe de domaine peut avoir autant **PublisherCatalog** des liens de relation que vous souhaitez lui donner.  
  
 Configurer la multiplicité d’un rôle en tapant sur le diagramme ou en modifiant le `Multiplicity` propriété dans le **propriétés** fenêtre. Le tableau suivant décrit les paramètres de cette propriété.  
  
|Type de multiplicité|Description|  
|-----------------------|-----------------|  
|0.. * (zéro à plusieurs)|Chaque instance de la classe de domaine peut avoir plusieurs instances de la relation ou aucune instance de la relation.|  
|Valeur&0;..&1; (zéro à un)|Chaque instance de la classe de domaine peut avoir pas plus d’une instance de la relation ou aucune instance de la relation.|  
|1..1 (un)|Chaque instance de la classe de domaine peut avoir une seule instance de la relation. Impossible de créer plusieurs instances de cette relation à partir de n’importe quelle instance de la classe de rôle. Si la validation est activée, une erreur de validation s’affiche lorsque n’importe quelle instance de la classe de rôle ne possède aucune instance de la relation.|  
|1.. * (un à plusieurs)|Chaque instance de la classe sur le rôle qui a cette multiplicité peut avoir plusieurs instances de la relation, et chaque instance doit avoir au moins une instance de la relation. Si la validation est activée, une erreur de validation s’affiche lorsque n’importe quelle instance de la classe de rôle ne possède aucune instance de la relation.|  
  
## <a name="domain-relationships-as-classes"></a>Relations de domaine en tant que Classes  
 Un lien est représenté dans le magasin en tant qu’instance de LinkElement, qui est une classe dérivée de l’élément de modèle. Vous pouvez définir ces propriétés dans le diagramme de modèle de domaine sur les relations de domaine.  
  
 Vous pouvez également rendre une relation source ou cible d’autres relations. Dans le diagramme de modèle de domaine avec le bouton droit de la relation de domaine, puis **afficher comme classe**. Une boîte de classe supplémentaires s’affiche. Vous pouvez ensuite connecter relations.  
  
 Vous pouvez définir une relation en partie par héritage, comme vous le faites avec les classes de domaine. Sélectionnez la relation dérivée et définissez **Base relation** dans la fenêtre Propriétés.  
  
 Une relation dérivée spécialisée sa relation de base. Le domaine des classes qu’il doivent être dérivés de liens ou le même que les classes liées par la relation de base. Lorsqu’un lien de la relation dérivée est créé dans un modèle, il est une instance de la dérivée et les relations de base. Dans le code de programme, vous pouvez accéder à l’extrémité opposée de la liaison en utilisant les propriétés générées par la base ou par la classe dérivée.  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)

