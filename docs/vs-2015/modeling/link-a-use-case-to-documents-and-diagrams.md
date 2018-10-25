---
title: Lier un cas d’usage à des documents et diagrammes | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2137863e48fbedfff4736588a6f3a177786aac57
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824501"
---
# <a name="link-a-use-case-to-documents-and-diagrams"></a>Lier un cas d'usage à des documents et diagrammes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez lier un cas d'usage dans un diagramme de cas d'usage à un autre diagramme ou document. Par exemple, vous pouvez lier le cas d'usage aux documents et diagrammes suivants :  
  
- un diagramme de séquence qui indique la façon dont les objectifs du cas d'usage sont atteints par des interactions entre les utilisateurs et le système ou ses principaux composants ;  
  
- un diagramme d'activités qui montre les actions détaillées des utilisateurs et du système ou de ses principaux composants lors de l'exécution du cas d'usage ;  
  
- une page ou un paragraphe OneNote qui décrit le cas d'usage en détail ;  
  
- un document Word ou une présentation PowerPoint qui décrit le cas d'usage en détail. Vous pouvez conserver ces documents dans la solution ou à un emplacement accessible par votre équipe, tel qu'un site SharePoint.  
  
  Pour lier un cas d'usage à un document, vous devez créer un artefact dans le diagramme de cas d'usage et connecter celui-ci à l'artefact. Dans les propriétés de l'artefact, vous définissez le chemin d'accès de l'autre diagramme ou document. Quand vous double-cliquez sur l'artefact, l'autre diagramme ou document s'ouvre.  
  
  Vous pouvez connecter autant d'artefacts que vous le souhaitez à chaque cas d'usage. Vous pouvez également lier des artefacts à d'autres types d'éléments dans un diagramme de cas d'usage.  
  
### <a name="to-open-a-document-associated-with-an-artifact"></a>Pour ouvrir un document associé à un artefact  
  
-   Dans le diagramme de cas d'usage, double-cliquez sur la forme de l'artefact.  
  
     Le document associé s'ouvre.  
  
### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Pour lier un cas d'usage à un diagramme ou à un fichier dans la même solution  
  
1.  Dessinez un diagramme (tel qu'un diagramme de séquence ou un diagramme d'activités) pour illustrer un scénario du cas d'usage.  
  
2.  Revenez au diagramme de cas d'usage.  
  
3.  Faites glisser le diagramme ou le fichier de l'Explorateur de solutions vers une partie vide du diagramme de cas d'usage.  
  
4.  Se connecter à partir de l’artefact à utilisation cas en utilisant un **dépendance**.  
  
### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Pour créer un lien vers un fichier de solution tel qu'un document Word ou une présentation PowerPoint  
  
1.  Ajoutez le document à la solution.  
  
    1.  Déplacez le document Word dans le même dossier Windows que la solution.  
  
    2.  Dans l’Explorateur de solutions, cliquez sur la solution, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
    3.  Accédez au document Word et cliquez sur **ajouter**.  
  
         Le document Word s'affiche dans un dossier de solution dans l'Explorateur de solutions.  
  
2.  Faites glisser le document Word de l'Explorateur de solutions vers une partie vide du diagramme de cas d'usage.  
  
     Un nouvel artefact s'affiche.  
  
3.  Se connecter à partir de l’artefact à utilisation cas en utilisant un **dépendance**.  
  
### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Pour créer un lien vers un élément OneNote, une page web ou un document partagé  
  
1.  Obtenez l'URL de l'élément partagé. Il peut s’agir, par exemple, un début de chemin d’accès de fichier réseau '\\\\», ou une page web ou URL Sharepoint commençant par « http:// » ou un lien vers une section OneNote, page ou un paragraphe de début « onenote : ».  
  
2.  Dans la boîte à outils, cliquez sur **artefact** puis cliquez sur dans le diagramme de cas d’usage.  
  
3.  Une fois le nouvel artefact sélectionné, tapez ou collez l’URL dans le **Hyperlink** propriété.  
  
    > [!NOTE]
    >  Si vous souhaitez fournir un chemin d’accès de fichier, il est préférable de choisir un fichier dans un espace de travail commun (commençant par «\\\\»), ou un fichier dans votre solution Visual Studio. Cela garantit que le chemin d'accès au fichier restera valide sur l'ordinateur d'un autre membre de l'équipe ou en cas de déplacement de la solution. Pour ajouter un document tel qu’un document Word à votre solution, avec le bouton droit de la solution dans l’Explorateur de solutions, pointez sur **ajouter** puis cliquez sur **élément existant**.  
  
## <a name="see-also"></a>Voir aussi  
 [Diagrammes de cas d’usage UML : référence](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md)   
 [Modifier des modèles UML et des diagrammes](../modeling/edit-uml-models-and-diagrams.md)   
 [Créer des modèles pour votre application](../modeling/create-models-for-your-app.md)



