---
title: Événements de build, page du Concepteur de projets (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a310de2e1fd754f16fd701f264f8d5ee8aac4166
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660944"
---
# <a name="build-events-page-project-designer-c"></a>Événements de build, page du Concepteur de projets (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez la page **Événements de build** du **Concepteur de projets** pour spécifier des instructions de configuration de build. Vous pouvez également spécifier les conditions dans lesquelles les événements post-build sont exécutés. Pour plus d’informations, consultez [Guide pratique pour spécifier des événements de build (C#)](../../ide/how-to-specify-build-events-csharp.md)et [Guide pratique pour spécifier des événements de build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur
 **Configuration** Ce contrôle n’est pas modifiable dans cette page. Pour obtenir une description de ce contrôle, consultez [Générer, page du Concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Plateforme** Ce contrôle n’est pas modifiable dans cette page. Pour obtenir une description de ce contrôle, consultez [Générer, page du Concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Ligne de commande de l’événement pré-build** Spécifie les commandes à exécuter avant le début de la génération. Pour taper de longues commandes, cliquez sur **Modifier pré-build** pour afficher la [boîte de dialogue Ligne de commande de l’événement pré-build/post-build](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Les événements pré-build ne fonctionnent pas si le projet est à jour et qu’aucune build n’est déclenchée.

 **Ligne de commande de l’événement post-build** Spécifie les commandes à exécuter à l’issue de la génération. Pour taper de longues commandes, cliquez sur **modifier après génération** pour afficher la boîte de **dialogue ligne de commande de l’événement pré-build/après génération**.

> [!NOTE]
> Ajoutez une instruction `call` avant toutes les commandes post-build qui exécutent des fichiers .bat.  Par exemple, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.

 **Exécuter l’événement post-build** Spécifie les conditions suivantes pour l’événement post-build à exécuter, comme indiqué dans le tableau ci-dessous.

|Option|Résultats|
|------------|------------|
|**Toujours**|L’événement post-build est exécuté, que la build ait abouti ou échoué.|
|**En cas de build réussie**|L’événement post-build est exécuté si la build réussit. Ainsi, l’événement est exécuté même pour un projet à jour, à condition que la build soit un succès.|
|**Lorsque la build met à jour la sortie du projet**|L’événement post-build n’est exécuté que quand le fichier de sortie du compilateur (.exe ou .dll) est différent du fichier de sortie précédent. Ainsi, un événement post-build n’est pas exécuté si un projet est à jour.|

## <a name="see-also"></a>Voir aussi
 [Comment : spécifier des événements de build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md) [Comment : spécifier des événements de build (C#)](../../ide/how-to-specify-build-events-csharp.md) [référence des propriétés de projet](../../ide/reference/project-properties-reference.md) [compilation et génération](../../ide/compiling-and-building-in-visual-studio.md)
