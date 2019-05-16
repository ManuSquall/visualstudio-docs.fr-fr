---
title: Présentation des modèles, des Classes et des relations | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
ms.assetid: 2ecd569c-b369-41ea-b78e-a61b62e2e4e9
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1809072ca0a01362e6434254b6e70a4bf4db4762
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698098"
---
# <a name="understanding-models-classes-and-relationships"></a>Présentation des modèles, des classes et des relations
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un langage spécifique à un domaine (DSL) est défini par son fichier de définition DSL, ainsi que tout code de programme personnalisé que vous pouvez écrire. La plupart du code du programme dans la solution DSL est généré à partir de ce fichier.  
  
 Cette rubrique décrit les fonctionnalités centrale de la définition DSL.  
  
## <a name="the-dsl-definition"></a>La définition DSL  
 Lorsque vous ouvrez `Dsl\DslDefinition.dsl`, votre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fenêtre ressemble à l’image suivante.  
  
 ![concepteur dsl](../modeling/media/dsl-designer.png "dsl_designer")  
  
 Les informations les plus importantes dans la définition DSL s’affiche dans le diagramme de définition DSL. Des informations supplémentaires, qui fait également partie de DslDefinition.dsl, s’affiche dans l’Explorateur DSL, qui apparaît généralement sur le côté du diagramme. Vous travaillez avec le schéma pour les tâches les plus fréquentes et avec l’Explorateur DSL pour les personnalisations plus avancées.  
  
 Le diagramme de définition DSL montre les classes de domaine qui définissent des éléments de modèle et les relations qui définissent des liens entre éléments de modèle. Il montre également les formes et connecteurs qui sont utilisées pour afficher les éléments de modèle à l’utilisateur.  
  
 ![concepteur dsl avec couloir](../modeling/media/dsl-desinger.png "dsl_desinger")  
  
 Lorsque vous sélectionnez un élément dans la définition DSL, dans le diagramme ou dans l’Explorateur DSL, les informations le concernant s’affiche dans la fenêtre Propriétés. Informations supplémentaires peuvent être affichées dans la fenêtre Détails DSL.  
  
### <a name="models-are-instances-of-dsls"></a>Les modèles sont des instances du DSL  
 Un *modèle* est une instance de votre DSL créé par un utilisateur. Un modèle contient des éléments de modèle, qui sont des instances des classes de domaine que vous définissez et des liens entre les éléments qui sont des instances des relations de domaine que vous définissez. Un modèle peut également avoir formes et connecteurs, qui affichent les éléments de modèle et les liens sur un diagramme. La définition DSL inclut les classes de forme, classes de connecteur et une classe pour le diagramme.  
  
 Une définition DSL est également appelé un *modèle de domaine*. Un modèle de définition DSL ou de domaine est la représentation au moment du design du langage spécifique à un domaine, tandis que le modèle est l’instanciation de l’exécution du langage spécifique à un domaine.  
  
## <a name="domain-classes-define-model-elements"></a>Classes de domaine définissent des éléments de modèle  
 Classes de domaine sont utilisés pour créer les différents éléments dans le domaine et relations de domaine sont les liens entre les éléments. Ils sont la représentation au moment du design des éléments et des liens qui seront instanciés par les utilisateurs du langage spécifique à la conception lorsqu’ils créent leurs modèles.  
  
 Cette illustration montre un modèle qui a été créé par l’utilisateur d’une bibliothèque DSL de la musique. Albums de musique sont représentées par des zones qui contiennent des listes de chansons. Artistes sont représentées par des zones aux angles arrondis et sont connectés aux albums auquel ils ont contribué.  
  
 ![Modèle d’instance du DSL généré](../modeling/media/music-instance.png "Music_Instance")  
  
 La définition DSL sépare deux aspects. L’apparence des éléments de modèle sur le diagramme de modèle est défini à l’aide des classes de formes et des classes de connecteur. Les informations contenues dans le modèle sont définies à l’aide des classes de domaine et les relations de domaine.  
  
 L’illustration suivante montre les classes de domaine et les relations dans la définition DSL de la bibliothèque de musique.  
  
 ![Relations d’incorporation et de référence](../modeling/media/music-classes.png "Music_Classes")  
  
 L’illustration montre quatre classes de domaine : Musique, Album, artiste et morceau. Les classes de domaine définissent les propriétés de domaine comme nom, titre et ainsi de suite. Dans le modèle d’instance, les valeurs de certaines de ces propriétés sont affichées dans le diagramme.  
  
 Entre les classes sont des relations de domaine : MusicHasAlbums MusicHasArtists, AlbumbHasSongs et ArtistAppearedOnAlbums. Les relations ont les multiplicités telles que 1..1, 0.. *. Par exemple, chaque chanson doit être associé à exactement un Album via la relation AlbumHasSongs. Chaque Album peut avoir autant de morceaux de musique.  
  
### <a name="rearranging-the-dsl-definition-diagram"></a>Réorganiser le diagramme de définition DSL  
 Notez qu’une classe de domaine peut apparaître plusieurs fois sur le diagramme de définition DSL, comme le fait Album dans cette image. Il y a toujours une vue principale, et il peut y avoir certains *référence* vues.  
  
 Pour réorganiser le diagramme de définition DSL, vous pouvez :  
  
- Échange principal et référencer des vues à l’aide de la **déplacer l’arborescence ici** et **fractionner l’arborescence** commandes. Cliquez sur une classe de domaine unique pour afficher ces commandes.  
  
- Réorganiser les classes de domaine et les classes de formes en appuyant sur Ctrl + haut et Ctrl + bas.  
  
- Réduire ou développer des classes à l’aide de l’icône en haut à droite de chaque forme.  
  
- Réduire les parties de l’arborescence en cliquant sur le signe moins (-) en bas d’une classe de domaine.  
  
## <a name="inheritance"></a>Héritage  
 Classes de domaine peuvent être définies à l’aide de l’héritage. Pour créer une dérivation de l’héritage, cliquez sur l’outil de l’héritage, cliquez sur la classe dérivée, puis cliquez sur la classe de base. Un élément de modèle possède toutes les propriétés qui sont définies sur sa propre classe de domaine, ainsi que toutes les propriétés héritées de la classe de base. Il hérite également ses rôles dans les relations.  
  
 L’héritage peut également servir entre les relations, formes et connecteurs. L’héritage doit conserver dans le même groupe. Une forme ne peut pas hériter d’une classe de domaine.  
  
## <a name="domain-relationships"></a>Relations de domaine  
 Éléments de modèle peuvent être liés par des relations. Des liens sont toujours binaires ; ils renvoient exactement deux éléments. Toutefois, n’importe quel élément peut avoir de nombreux liens vers d’autres objets, et il peut même y avoir plus d’un lien entre la même paire d’éléments.  
  
 Tout comme vous pouvez définir différentes classes d’éléments, vous pouvez définir différentes classes de liens. La classe d’un lien est appelée un *relation de domaine*. Une relation de domaine spécifie les classes d’élément de ses instances peuvent se connecter. Chaque extrémité d’une relation est appelée un *rôle*, et la relation de domaine définit les noms pour les deux rôles, ainsi que pour la relation proprement dite.  
  
 Il existe deux types de relations de domaine : incorporation de relations et référence. Sur le diagramme de définition DSL, relations d’incorporation ont des lignes pleines à chaque rôle et les relations de référence ont des lignes en pointillés.  
  
### <a name="embedding-relationships"></a>Relations d’incorporation  
 Chaque élément dans un modèle, à l’exception de sa racine, est la cible d’un lien d’incorporation. Par conséquent, l’ensemble du modèle forme une arborescence unique de l’incorporation des liens. Une relation d’incorporation représente la relation contenant-contenu ou la propriété. Deux éléments de modèle qui sont liés de cette façon sont également appelés parents et enfants. L’enfant est dit à incorporer dans le parent.  
  
 Incorporation des liens généralement ne figurent pas explicitement en tant que connecteurs dans un diagramme. Au lieu de cela, elles sont généralement représentées par la relation contenant-contenu. La racine du modèle est représentée par le diagramme et les éléments incorporés qu’il contient sont affichés sous forme de formes sur le diagramme.  
  
 Dans l’exemple, la classe racine Music a une relation d’incorporation MusicHasAlbums à Album, ce qui a une incorporation AlbumHasSongs chanson. Chansons sont affichés en tant qu’éléments dans une liste à l’intérieur de chaque Album. Musique a également une incorporation MusicHasArtists à la classe de l’artiste, dont les instances s’affichent également en tant que formes sur le diagramme.  
  
 Par défaut, les éléments incorporés sont automatiquement supprimés lorsque leurs parents sont supprimés.  
  
 Lorsqu’un modèle est enregistré pour le fichier au format XML, les éléments incorporés sont imbriquées dans leurs parents, sauf si vous avez personnalisé la sérialisation.  
  
> [!NOTE]
> L'incorporation n'est pas la même chose que l'héritage. Les enfants dans une relation d’incorporation n’héritent pas les propriétés du parent. Une incorporation est un type de lien entre les éléments de modèle. L’héritage est une relation entre les classes et ne crée pas de liens entre éléments de modèle.  
  
### <a name="embedding-rules"></a>Incorporation des règles  
 Chaque élément dans un modèle d’instance doit être la cible d’un seul lien d’incorporation, à l’exception de la racine du modèle.  
  
 Par conséquent, chaque classe de domaine non abstraite, à l’exception de la classe racine, doit être la cible d’au moins une relation d’incorporation, ou il doit hériter d’une imbrication à partir d’une classe de base. Une classe peut être la cible des incorporations de deux ou plus, mais ses éléments de modèle d’instance n’admet qu’un seul parent à la fois. La multiplicité de la cible à la source doit être la valeur 0.. 1 ou 1.. 1.  
  
### <a name="the-explorer-displays-the-embedding-tree"></a>L’Explorateur affiche l’arborescence d’incorporation  
 Votre définition DSL crée également un Explorateur, les utilisateurs voient en même temps que leur schéma de modèle.  
  
 ![Explorateur généré de DSL](../modeling/media/music-explorer.png "Music_Explorer")  
  
 L’Explorateur affiche tous les éléments dans le modèle, y compris ceux pour lesquels vous n’avez pas défini de toutes les formes. Il affiche des éléments et des relations d’incorporation, mais pas les relations de référence.  
  
 Pour afficher les valeurs des propriétés de domaine d’un élément, l’utilisateur sélectionne un élément, dans le diagramme de modèle ou dans l’Explorateur de modèles et ouvre la fenêtre Propriétés. Il affiche toutes les propriétés de domaine, y compris ceux qui ne sont pas affichés sur le diagramme. Dans l’exemple, chaque chanson a un titre et un Genre, mais uniquement la valeur du titre est affichée sur le diagramme.  
  
## <a name="reference-relationships"></a>Relations de référence  
 Une relation de référence représente n’importe quel type de relation qui n’est pas l’incorporation.  
  
 Relations de référence sont généralement affichées sur un diagramme en tant que connecteurs entre les formes.  
  
 Dans la représentation XML du modèle, un lien de référence entre deux éléments est représenté à l’aide de *monikers.* Autrement dit, les monikers sont des noms qui identifient de façon unique chaque élément dans le modèle. Le nœud XML pour chaque élément de modèle contient un nœud qui spécifie le nom de la relation et le moniker de l’autre élément.  
  
## <a name="roles"></a>Rôles  
 Chaque relation de domaine a deux rôles, un rôle de source et un rôle cible.  
  
 Dans l’image suivante, la ligne entre le **Publisher** de classe de domaine et le **PublisherCatalog** relation de domaine est le rôle source. La ligne entre la relation de domaine et le **Album** classe de domaine est le rôle cible.  
  
 ![Les rôles et les propriétés. ](../modeling/media/propertycode.png "PropertyCode")  
  
 Les noms associés à une relation sont particulièrement importants lorsque vous écrivez du code de programme qui parcourt le modèle. Par exemple, lorsque vous générez la solution DSL, la classe générée Publisher a une propriété de catalogue qui est une collection d’Albums. La classe Album a une propriété de serveur de publication qui est une instance unique de la classe du serveur de publication.  
  
 Lorsque vous créez une relation dans une définition DSL, les noms de propriété et de relation sont des valeurs par défaut. Toutefois, vous pouvez les modifier.  
  
## <a name="multiplicities"></a>Multiplicités  
 Multiplicités spécifient le nombre d’éléments peut avoir le même rôle dans une relation de domaine. Dans l’exemple, le zéro-à-plusieurs (0..\*) paramètre de multiplicité sur le **catalogue** rôle spécifie que n’importe quelle instance de la **Publisher** de classe de domaine peut avoir autant  **PublisherCatalog** liens de relation que vous le souhaitez afin de lui donner.  
  
 Configurer la multiplicité d’un rôle en tapant sur le diagramme ou en modifiant le `Multiplicity` propriété dans le **propriétés** fenêtre. Le tableau suivant décrit les paramètres de cette propriété.  
  
|Type de multiplicité|Description|  
|-----------------------|-----------------|  
|0.. * (zéro à plusieurs)|Chaque instance de la classe de domaine peut avoir plusieurs instances de la relation ou aucune instance de la relation.|  
|Valeur 0.. 1 (zéro à un)|Chaque instance de la classe de domaine peut avoir pas plus d’une instance de la relation ou aucune instance de la relation.|  
|1..1 (un)|Chaque instance de la classe de domaine peut avoir une instance de la relation. Impossible de créer plusieurs instances de cette relation à partir de n’importe quelle instance de la classe de rôle. Si la validation est activée, une erreur de validation s’affiche lorsque n’importe quelle instance de la classe de rôle n’a aucune instance de la relation.|  
|1.. * (un à plusieurs)|Chaque instance de la classe sur le rôle qui a cette multiplicité peut avoir plusieurs instances de la relation, et chaque instance doit avoir au moins une instance de la relation. Si la validation est activée, une erreur de validation s’affiche lorsque n’importe quelle instance de la classe de rôle n’a aucune instance de la relation.|  
  
## <a name="domain-relationships-as-classes"></a>Relations de domaine en tant que Classes  
 Un lien est représenté dans le Store en tant qu’instance de LinkElement, qui est une classe dérivée de ModelElement. Vous pouvez définir ces propriétés dans le diagramme de modèle de domaine sur les relations de domaine.  
  
 Vous pouvez également rendre une relation source ou cible d’autres relations. Dans le diagramme de modèle de domaine, avec le bouton droit de la relation de domaine, puis sélectionnez **afficher en tant que la classe**. Une boîte de classes supplémentaires s’affiche. Vous pouvez ensuite connecter relations.  
  
 Vous pouvez définir une relation en partie par héritage, tout comme vous pouvez le faire avec les classes de domaine. Sélectionnez la relation dérivée et définissez **Base relation** dans la fenêtre Propriétés.  
  
 Une relation dérivée spécialisée sa relation de base. Le domaine des classes qu’il doivent être dérivés de liens ou le même que les classes liées par la relation de base. Création d’un lien de la relation dérivée dans un modèle, il est une instance de la dérivée et les relations de base. Dans le code de programme, vous pouvez accéder à l’extrémité opposée du lien en utilisant les propriétés générées par la base ou par la classe dérivée.  
  
## <a name="see-also"></a>Voir aussi  
 [Relations de domaine dans l’API générée](../misc/domain-relationships-in-the-generated-api.md)   
 [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
