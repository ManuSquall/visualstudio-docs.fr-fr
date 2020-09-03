---
title: Événements de build, boîte de dialogue (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- build events, specifying
- pre-build events
- Build Events dialog box
- post-build events
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9fa3b4365f49d172e077ca132b26a49580228c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660956"
---
# <a name="build-events-dialog-box-visual-basic"></a>Événements de build, boîte de dialogue (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez la boîte de dialogue **Événements de build** pour spécifier des instructions de configuration de build. Vous pouvez également spécifier les conditions dans lesquelles les événements pré-build ou post-build sont exécutés. Pour plus d’informations, consultez [Guide pratique pour spécifier des événements de build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

 **Ligne de commande de l’événement pré-build** Spécifie les commandes à exécuter avant le début de la génération. Pour taper de longues commandes, cliquez sur **Modifier pré-build** pour afficher la [boîte de dialogue Ligne de commande de l’événement pré-build/post-build](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Les événements pré-build ne s’exécutent pas si le projet est à jour et qu’aucune build n’est déclenchée.

 **Ligne de commande de l’événement post-build** Spécifie les commandes à exécuter à l’issue de la génération. Pour taper de longues commandes, cliquez sur **Modifier post-build** pour afficher la **boîte de dialogue Ligne de commande de l’événement pré-build/post-build**.

> [!NOTE]
> Ajoutez une instruction `call` avant toutes les commandes post-build qui exécutent des fichiers .bat.  Par exemple, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.

 **Exécuter l’événement post-build** Spécifie les conditions pour l’événement post-build à exécuter, comme indiqué dans le tableau ci-dessous.

|Option|Résultats|
|------------|------------|
|**Toujours**|L’événement post-build est exécuté, que la build ait abouti ou échoué.|
|**En cas de build réussie**|L’événement post-build est exécuté si la build réussit. L’événement est exécuté même pour un projet à jour, à condition que la build soit un succès. Il s'agit du paramètre par défaut.|
|**Lorsque la build met à jour la sortie du projet**|L’événement post-build n’est exécuté que quand le fichier de sortie du compilateur (.exe ou .dll) est différent du fichier de sortie précédent. Un événement post-build n’est pas exécuté si un projet est à jour.|

## <a name="see-also"></a>Voir aussi
 [Page compiler, concepteur de projets (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) [Comment : spécifier des événements de build (Visual Basic) boîte de](../../ide/how-to-specify-build-events-visual-basic.md) [dialogue ligne de commande de l’événement pré-build/après génération](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
