---
title: Décrire le flux de contrôle avec des fragments dans les diagrammes de séquence UML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.interactionoperand
- vs.teamarch.sequencediagram.combinedfragment
helpviewer_keywords:
- UML sequence diagrams, control flow
- UML sequence diagrams, fragments
- sequence diagrams, fragments
- sequence diagrams, control flow
ms.assetid: efcc0949-be7e-4cf4-99ef-47c36b3803ae
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4ab4c65e554e9eef75a1761719ce19f3312e07ce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727650"
---
# <a name="describe-control-flow-with-fragments-on-uml-sequence-diagrams"></a>Décrire le flux de contrôle à l'aide de fragments dans les diagrammes de séquence UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans un diagramme de séquence UML, les *fragments combinés* vous permettent d’afficher des boucles, des branches et d’autres éléments.  
  
 Un fragment combiné se compose d’un ou de plusieurs *opérandes d’interaction*, chacun d’entre eux contenant un ou plusieurs messages, utilisations d’interactions ou encore fragments combinés.  
  
> [!NOTE]
>  Cette rubrique traite des fragments dans les diagrammes de séquence. Pour plus d’informations sur la lecture des diagrammes de séquence UML, consultez [diagrammes de séquence UML : référence](../modeling/uml-sequence-diagrams-reference.md). Pour plus d’informations sur le dessin des diagrammes de séquence UML, consultez [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 ![Fragment avec deux opérandes d’Interaction combiné](../modeling/media/uml-seqfragments.png "UML_SeqFragments")  
  
 Les éléments présentés dans l’illustration sont les suivants :  
  
1.  Fragment combiné. Il existe plusieurs genres de fragments combinés. Cet exemple est un fragment combiné Alt que vous pouvez utiliser pour montrer que d’autres séquences de messages peuvent se produire.  
  
2.  Opérandes d’interaction. Chaque fragment combiné contient au moins un opérande d’interaction qui peut contenir des messages, des utilisations d’interaction et de plus petits fragments combinés. Dans cet exemple, le fragment combiné Alt comprend deux opérations d’interaction, affichant deux autres séquences de messages.  
  
3.  Vous pouvez sélectionner chaque opérande d’interaction individuellement en cliquant dessus. Dans cet exemple, l’opérande d’interaction supérieur est sélectionné afin que sa limite puisse être affichée. En règle générale, seule la ligne de séparation entre les opérandes d’interaction est visible.  
  
    > [!NOTE]
    >  Pour sélectionner l’opérande d’interaction supérieur, vous ne devez pas cliquer trop près de la partie supérieure du fragment combiné.  
  
4.  Gardes. Vous pouvez attribuer un garde à chaque opérande d’interaction. Celui-ci décrit la condition sous laquelle les messages contenus dans l’opérande d’interaction sont exécutés.  
  
## <a name="creating-combined-fragments"></a>Création de fragments combinés  
 Pour obtenir la liste des genres de fragments que vous pouvez créer, consultez [Genres de fragments combinés](#KindsOfFragment).  
  
#### <a name="to-create-a-combined-fragment"></a>Pour créer un fragment combiné  
  
1. Sélectionnez un message ou une séquence de messages qui partent tous de la même ligne de vie ou occurrence d’exécution.  
  
   > [!NOTE]
   >  Si vous sélectionnez plusieurs messages, ceux-ci doivent former une séquence ininterrompue.  
  
2. Cliquez avec le bouton droit sur l’un des messages, pointez sur **Entourer de**, puis cliquez sur le genre de fragment combiné de votre choix tel que **Fragment combiné Alt**.  
  
    Un nouveau fragment combiné apparaît. Le titre indique le genre de fragment combiné que vous avez sélectionné, comme **Alt**.  
  
    Le fragment combiné comprend un fragment contenant les messages que vous avez sélectionnés.  
  
   Vous pouvez ajouter d’autres opérandes d’interaction à certains genres de fragments combinés.  
  
   Après avoir réorganisé les messages dans un fragment combiné, sélectionnez **Réorganiser la disposition** dans le menu contextuel pour redimensionner le frame de fragment combiné.  
  
#### <a name="to-add-a-new-interaction-operand-to-a-combined-fragment"></a>Pour ajouter un nouvel opérande d’interaction à un fragment combiné  
  
1. Cliquez avec le bouton droit dans un espace vide dans l’opérande d’interaction (2), hors de tout fragment contenu et en dessous du titre du fragment combiné.  
  
2. Pointez sur **Ajouter**.  
  
3. Cliquez sur **Opérande d’interaction avant**ou **Opérande d’interaction après**.  
  
4. Vous pouvez ajouter des messages dans le nouvel opérande d’interaction à l’aide des outils de messages, ou en copiant et collant des messages existants.  
  
   Vous pouvez définir la propriété **Guard** d’un opérande d’interaction pour décrire les conditions dans lesquelles les messages qu’il contient sont exécutés. Par exemple, dans un fragment combiné **Loop** , vous pouvez utiliser le garde pour spécifier la condition pendant laquelle la boucle continue. Dans un fragment combiné **Alt** , vous pouvez spécifier une condition distincte pour chaque opérande d’interaction.  
  
#### <a name="to-set-the-guard-of-an-interaction-operand"></a>Pour définir le garde d’un opérande d’interaction  
  
1. Cliquez dans un espace vide de l’opérande d’interaction (2), hors de tout fragment contenu.  
  
    Une bordure de sélection apparaît autour de l’opérande d’interaction et de la condition de garde.  
  
    Le titre dans la fenêtre **Propriétés** affiche **Opérande d’interaction**.  
  
2. Tapez la condition de garde.  
  
    La condition apparaît près de la partie supérieure du fragment (4).  
  
   Vous pouvez définir les propriétés de certains genres de fragments combinés.  
  
#### <a name="to-set-or-view-the-properties-of-a-combined-fragment"></a>Pour définir ou afficher les propriétés d’un fragment combiné  
  
-   Cliquez avec le bouton droit sur le titre du fragment combiné, puis cliquez sur **Propriétés**.  
  
    > [!NOTE]
    >  Les différents genres de fragments combinés possèdent des propriétés différentes.  
  
##  <a name="KindsOfFragment"></a> Genres de fragments combinés  
  
### <a name="fragments-describing-control-flow"></a>Fragments décrivant le flux de contrôle  
 Un diagramme de séquence simple affiche une seule séquence type. Vous pouvez utiliser les types suivants de fragments combinés pour décrire des variations qui peuvent se produire en différentes occasions.  
  
|Type de fragment|Description|  
|-------------------|-----------------|  
|**opt**|Facultatif. Contient une séquence qui peut ou non se produire. Dans le garde, vous pouvez spécifier la condition sous laquelle elle se produit.|  
|**Alt**|Contient une liste des fragments contenant d’autres séquences de messages. Une seule séquence peut se produire à la fois.<br /><br /> Vous pouvez insérer un garde dans chaque fragment pour indiquer la condition sous laquelle il peut s’exécuter. Un garde **else** indique un fragment qui doit s’exécuter si aucun autre garde n’a la valeur True. Si tous les gardes ont la valeur False et qu’il n’existe aucun **else**, aucun des fragments n’est exécuté.|  
|**Loop**|Le fragment est répété un certain nombre de fois. Dans le garde, vous pouvez indiquer la condition sous laquelle il doit être répété.<br /><br /> Les fragments combinés Loop possèdent des propriétés **Min** et **Max**qui indiquent les nombres minimum et maximum de fois que le fragment peut être répété. Par défaut, il n’y a aucune restriction.|  
|**Break**|Si ce fragment est exécuté, le reste de la séquence est abandonné. Vous pouvez utiliser le garde pour indiquer la condition dans laquelle l’arrêt se produit.|  
|**Par**|Parallel. Les événements des fragments peuvent être entrelacés.|  
|**Critique**|Utilisé dans un fragment Par ou Seq. Indique que les messages dans ce fragment ne doivent pas être entrelacés avec d’autres messages.|  
|**Seq**|Il existe au moins deux fragments d’opérande. Les messages impliquant la même ligne de vie doivent se produire dans l’ordre des fragments. Quand ils n’impliquent pas les mêmes lignes de vie, les messages des différents fragments peuvent être entrelacés en parallèle.|  
|**Strict**|Il existe au moins deux fragments d’opérande. Les fragments doivent se produire dans l’ordre indiqué.|  
  
### <a name="fragments-about-how-to-interpret-the-sequence"></a>Fragments concernant l’interprétation de la séquence  
 Par défaut, le diagramme de séquence déclare une série de messages qui peuvent se produire. Dans le système en cours d’exécution, d’autres messages que vous n’avez pas choisi d’afficher dans le diagramme peuvent se produire.  
  
 Les types de fragments suivants peuvent être utilisés pour modifier cette interprétation.  
  
|Type de fragment|Description|  
|-------------------|-----------------|  
|**Prendre en compte**|Spécifie une liste des messages que ce fragment décrit. D’autres messages peuvent se produire dans le système en cours d’exécution, mais ils ne sont pas significatifs aux fins de cette description.<br /><br /> Tapez la liste dans la propriété **Messages** .|  
|**Ignorer**|Liste des messages que ce fragment ne décrit pas. Ils peuvent se produire dans le système en cours d’exécution, mais ils ne sont pas significatifs aux fins de cette description.<br /><br /> Tapez la liste dans la propriété **Messages** .|  
|**Assert**|Le fragment d’opérande spécifie les seules séquences valides. Il est généralement utilisé dans un fragment Consider ou Ignore.|  
|**neg**|La séquence affichée dans ce fragment ne doit pas se produire. Il est généralement utilisé dans un fragment Consider ou Ignore.|  
  
## <a name="see-also"></a>Voir aussi  
 [Diagrammes de séquence UML : indications](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Diagrammes de séquence UML : référence](../modeling/uml-sequence-diagrams-reference.md)   
 [Modifier des modèles et des diagrammes UML](../modeling/edit-uml-models-and-diagrams.md)



