---
title: Événements de build, page du Concepteur de projets (C#)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 49edb08b35b3006901201ccc880a5e74da92f834
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948314"
---
# <a name="build-events-page-project-designer-c"></a>Événements de build, page du Concepteur de projets (C#)
Utilisez la page **Événements de build** du **Concepteur de projets** pour spécifier des instructions de configuration de build. Vous pouvez également spécifier les conditions dans lesquelles les événements post-build sont exécutés. Pour plus d'informations, voir [Procédure : Spécifier des événements de build (C#)](../../ide/how-to-specify-build-events-csharp.md) et [Guide pratique pour spécifier des événements de build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>Liste des éléments d’interface
 **Configuration** Ce contrôle n’est pas modifiable dans cette page. Pour obtenir une description de ce contrôle, consultez [Générer, page du Concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Plateforme** Ce contrôle n’est pas modifiable dans cette page. Pour obtenir une description de ce contrôle, consultez [Générer, page du Concepteur de projets (C#)](../../ide/reference/build-page-project-designer-csharp.md).

 **Ligne de commande de l’événement pré-build** Spécifie les commandes à exécuter avant le début de la génération. Pour taper de longues commandes, cliquez sur **Modifier pré-build** pour afficher la [boîte de dialogue Ligne de commande de l’événement pré-build/post-build](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Les événements pré-build ne fonctionnent pas si le projet est à jour et qu’aucune build n’est déclenchée.


 **Ligne de commande de l’événement post-build** Spécifie les commandes à exécuter à l’issue de la génération. Pour taper de longues commandes, cliquez sur **Modifier post-build** pour afficher la **boîte de dialogue Ligne de commande de l’événement pré-build/post-build**.

> [!NOTE]
> Ajoutez une instruction `call` avant toutes les commandes post-build qui exécutent des fichiers .bat. Par exemple, `call C:\MyFile.bat` ou `call C:\MyFile.bat call C:\MyFile2.bat`.


 **Exécuter l’événement post-build** Spécifie les conditions suivantes pour l’événement post-build à exécuter, comme indiqué dans le tableau ci-dessous.

|Option|Résultat|
|------------|------------|
|**Toujours**|L’événement post-build est exécuté, que la build ait abouti ou échoué.|
|**En cas de build réussie** |L’événement post-build est exécuté si la build réussit. Ainsi, l’événement est exécuté même pour un projet à jour, à condition que la build soit un succès.|
|**Lorsque la build met à jour la sortie du projet**|L’événement post-build n’est exécuté que quand le fichier de sortie du compilateur (.exe ou .dll) est différent du fichier de sortie précédent. Ainsi, un événement post-build n’est pas exécuté si un projet est à jour.|

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Spécifier des événements de build (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Guide pratique pour spécifier des événements de build (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Informations de référence sur les propriétés de projet](../../ide/reference/project-properties-reference.md)
- [Compilation et génération](../../ide/compiling-and-building-in-visual-studio.md)