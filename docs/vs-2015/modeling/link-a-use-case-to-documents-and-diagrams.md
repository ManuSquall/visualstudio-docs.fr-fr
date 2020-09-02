---
title: Lier un cas d’usage à des documents et des diagrammes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c713759a8ea75eed3048469327f962668efa4f70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657642"
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

- Dans le diagramme de cas d'usage, double-cliquez sur la forme de l'artefact.

     Le document associé s'ouvre.

### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Pour lier un cas d'usage à un diagramme ou à un fichier dans la même solution

1. Dessinez un diagramme (tel qu'un diagramme de séquence ou un diagramme d'activités) pour illustrer un scénario du cas d'usage.

2. Revenez au diagramme de cas d'usage.

3. Faites glisser le diagramme ou le fichier de l'Explorateur de solutions vers une partie vide du diagramme de cas d'usage.

4. Connectez-vous de l’artefact au cas d’usage à l’aide d’une **dépendance**.

### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Pour créer un lien vers un fichier de solution tel qu'un document Word ou une présentation PowerPoint

1. Ajoutez le document à la solution.

    1. Déplacez le document Word dans le même dossier Windows que la solution.

    2. Dans Explorateur de solutions, cliquez avec le bouton droit sur la solution, pointez sur **Ajouter**, puis cliquez sur **élément existant**.

    3. Accédez au document Word, puis cliquez sur **Ajouter**.

         Le document Word s'affiche dans un dossier de solution dans l'Explorateur de solutions.

2. Faites glisser le document Word de l'Explorateur de solutions vers une partie vide du diagramme de cas d'usage.

     Un nouvel artefact s'affiche.

3. Connectez-vous de l’artefact au cas d’usage à l’aide d’une **dépendance**.

### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Pour créer un lien vers un élément OneNote, une page web ou un document partagé

1. Obtenez l'URL de l'élément partagé. Il peut s’agir, par exemple, d’un chemin d’accès au fichier réseau commençant par « \\ \\ », d’une page Web ou d’une URL SharePoint commençant par « http:// », ou d’un lien vers une section, une page ou un paragraphe OneNote commençant par « OneNote : ».

2. Dans la boîte à outils, cliquez sur **artefact** , puis cliquez dans le diagramme de cas d’usage.

3. Après avoir sélectionné le nouvel artefact, tapez ou collez l’URL dans la propriété **lien hypertexte** .

    > [!NOTE]
    > Si vous souhaitez fournir un chemin d’accès de fichier, il est préférable de choisir un fichier dans un espace de travail commun (à partir de « \\ \\ ») ou un fichier dans votre solution Visual Studio. Cela garantit que le chemin d'accès au fichier restera valide sur l'ordinateur d'un autre membre de l'équipe ou en cas de déplacement de la solution. Pour ajouter un document tel qu’un document Word à votre solution, cliquez avec le bouton droit sur la solution dans Explorateur de solutions, pointez sur **Ajouter** , puis cliquez sur **élément existant**.

## <a name="see-also"></a>Voir aussi
 [Diagrammes de cas d’usage UML : référence](../modeling/uml-use-case-diagrams-reference.md) [diagrammes de cas d’usage UML : instructions](../modeling/uml-use-case-diagrams-guidelines.md) [modifier des modèles et des diagrammes UML](../modeling/edit-uml-models-and-diagrams.md) [créer des modèles pour votre application](../modeling/create-models-for-your-app.md)
