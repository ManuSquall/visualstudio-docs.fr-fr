---
title: Journalisation dans MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 80a73f2433f942c35413f77143203c06cd9447a5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="logging-in-msbuild"></a>Journalisation dans MSBuild
La journalisation vous permet de surveiller la progression d’une génération. Elle capture dans un fichier journal les événements, messages, avertissements et erreurs liés à la génération.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Obtention de journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)  
 Décrit les différents aspects de la journalisation dans [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 [Enregistreurs d’événements de génération](../msbuild/build-loggers.md)  
 Décrit les étapes requises pour créer un enregistreur d’événements dans un environnement monoprocesseur.  
  
 [Journalisation dans un environnement multiprocesseur](../msbuild/logging-in-a-multi-processor-environment.md)  
 Décrit le fonctionnement de la journalisation dans un environnement multiprocesseur ainsi que les deux modèles de journalisation multiprocesseur.  
  
 [Écriture d’enregistreurs d’événements prenant en charge plusieurs processeurs](../msbuild/writing-multi-processor-aware-loggers.md)  
 Décrit la création d’enregistreurs d’événements prenant en charge plusieurs processeurs, ainsi que l’utilisation de ConfigurableForwardingLogger.  
  
 [Création d’enregistreurs d’événements de transfert](../msbuild/creating-forwarding-loggers.md)  
 Décrit la création de journaux de transfert personnalisés.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Génération parallèle de plusieurs projets](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)  
 Explique comment générer plus rapidement plusieurs projets en les exécutant en parallèle.