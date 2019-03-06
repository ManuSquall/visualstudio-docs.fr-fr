---
title: Journalisation dans MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99bbb6ba880ace8b21ae6b6009ee84cffee79485
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618729"
---
# <a name="logging-in-msbuild"></a>Journalisation dans MSBuild
La journalisation vous permet de surveiller la progression d’une génération. Elle capture dans un fichier journal les événements, messages, avertissements et erreurs liés à la génération.

## <a name="in-this-section"></a>Dans cette section
- [Obtenir des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)

 Décrit les différents aspects de la journalisation dans [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

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