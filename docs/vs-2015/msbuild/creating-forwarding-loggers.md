---
title: Création de journaux de transfert | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ecc9bae7176c0d8c0f79452baff87a7a697db459
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648219"
---
# <a name="creating-forwarding-loggers"></a>Création de journaux de transfert
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les journaux de transfert améliorent l’efficacité de la journalisation en vous permettant de choisir les événements que vous voulez suivre quand vous générez des projets sur un système multiprocesseur. En activant les journaux de transfert, vous pouvez empêcher des événements indésirables de submerger le journal central, de ralentir la génération et d’encombrer votre journal.  
  
 Pour créer un journal de transfert, vous pouvez implémenter l’interface <xref:Microsoft.Build.Framework.IForwardingLogger>, puis implémenter ses méthodes manuellement ou utiliser la classe <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> et ses méthodes préconfigurées. (L’utilisation de cette classe est suffisante pour la plupart des applications.)  
  
## <a name="register-events-and-respond-to-them"></a>Inscrire les événements et y répondre  
 Un journal de transfert rassemble des informations sur les événements de génération tels qu’ils sont signalés par le moteur de génération secondaire, qui est un processus de travail créé par le processus de génération principal lors d’une génération sur un système multiprocesseur. Le journal de transfert sélectionne ensuite les événements à transférer au journal central, en fonction des instructions qui vous lui avez données.  
  
 Vous devez inscrire les journaux de transfert pour gérer les événements que vous voulez suivre. Pour s’inscrire à des événements, les journaux doivent remplacer la méthode <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>. Cette méthode inclut maintenant un paramètre facultatif, `nodecount`, qui peut être défini sur le nombre de processeurs dans le système. (Par défaut, la valeur est 1.)  
  
 <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> et <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> sont des exemples d’événements que vous pouvez suivre.  
  
 Dans un environnement multiprocesseur, les messages d’événement peuvent arriver dans le désordre. Vous devez donc évaluer les événements en utilisant le gestionnaire d’événements dans le journal de transfert et le programmer de façon à déterminer quels événements passer au redirecteur pour les transférer au journal central. Pour cela, vous pouvez utiliser la classe <xref:Microsoft.Build.Framework.BuildEventContext> qui est attachée à chaque message, pour identifier les événements que vous voulez transférer, puis passer les noms des événements à la classe <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> (ou à une de ses sous-classes). Quand vous utilisez cette méthode, aucun autre code spécifique n’est nécessaire pour transférer des événements.  
  
## <a name="specify-a-forwarding-logger"></a>Spécifier un journal de transfert  
 Une fois que le journal de transfert a été compilé en assembly, vous devez indiquer à [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] qu’il faut l’utiliser lors des générations. Pour cela, utilisez les commutateurs `/FileLogger`, `/FileLoggerParameters` et `/DistributedFileLogger` avec MSBuild.exe. Le commutateur `/FileLogger` indique à MSBuild.exe que le journal est directement attaché. Le commutateur `/DistributedFileLogger` signifie qu’il existe un fichier journal par nœud. Pour définir des paramètres sur le journal de transfert, utilisez le commutateur `/FileLoggerParameters`. Pour plus d’informations sur ces commutateurs et sur d’autres commutateurs de MSBuild.exe, consultez [Informations de référence sur la ligne de commande](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="multi-processor-aware-loggers"></a>Journaux pour les systèmes multiprocesseurs  
 Quand vous générez un projet sur un système multiprocesseur, les messages de génération provenant de chaque processeur ne sont pas automatiquement entrelacés dans une séquence unifiée. Vous devez donc établir une priorité de regroupement des messages avec la classe <xref:Microsoft.Build.Framework.BuildEventContext> qui est attachée à chaque message. Pour plus d’informations sur la génération multiprocesseur, consultez [Journalisation dans un environnement multiprocesseur](../msbuild/logging-in-a-multi-processor-environment.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Obtention de journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Enregistreurs d’événements de génération](../msbuild/build-loggers.md)   
 [Journalisation dans un environnement multiprocesseur](../msbuild/logging-in-a-multi-processor-environment.md)
