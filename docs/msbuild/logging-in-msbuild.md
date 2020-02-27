---
title: Journalisation dans MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a66164426b760798571fc35e5288158a8dae9943
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633549"
---
# <a name="logging-in-msbuild"></a>Journalisation dans MSBuild

La journalisation vous permet de surveiller la progression d’une génération. Elle capture dans un fichier journal les événements, messages, avertissements et erreurs liés à la génération.

## <a name="in-this-section"></a>Contenu de cette section

- [Obtenir des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)

 Décrit les différents aspects de la journalisation dans MSBuild.

- [Enregistreurs d’événements de génération](../msbuild/build-loggers.md)

 Décrit les étapes requises pour créer un enregistreur d’événements dans un environnement monoprocesseur.

- [Journalisation dans un environnement multiprocesseur](../msbuild/logging-in-a-multi-processor-environment.md)

 Décrit le fonctionnement de la journalisation dans un environnement multiprocesseur ainsi que les deux modèles de journalisation multiprocesseur.

- [Écrire des enregistreurs d’événements prenant en charge plusieurs processeurs](../msbuild/writing-multi-processor-aware-loggers.md)

 Décrit la création d’enregistreurs d’événements prenant en charge plusieurs processeurs, ainsi que l’utilisation de ConfigurableForwardingLogger.

- [Créer des journaux de transfert](../msbuild/creating-forwarding-loggers.md)

 Décrit la création de journaux de transfert personnalisés.

## <a name="see-also"></a>Voir aussi

- [Générer plusieurs projets en parallèle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) Explique comment générer plus rapidement plusieurs projets en les exécutant en parallèle.
