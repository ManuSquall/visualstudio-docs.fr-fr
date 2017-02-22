---
title: "Creating Forwarding Loggers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, forwarding loggers"
  - "MSBuild, logging"
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Creating Forwarding Loggers
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les journaux de transfert améliorent l'efficacité de la journalisation en vous permettant de choisir les événements à contrôler lors de la génération de projets sur un système multiprocesseur.  En activant les journaux de transfert, vous pouvez éviter d'encombrer le journal central d'événements inutiles, ce qui ralentit la génération et sature votre journal.  
  
 Pour créer un journal de transfert, vous pouvez soit implémenter l'interface <xref:Microsoft.Build.Framework.IForwardingLogger> puis ses méthodes manuellement, soit utiliser la classe <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> et ses méthodes préconfigurées.  \(La dernière approche suffit pour la plupart des applications.\)  
  
## Enregistrement et réponse aux événements  
 Un journal de transfert rassemble des informations à propos des événements de build signalés par le moteur de génération secondaire qui est un processus de travail créé par le processus de génération principal pendant un build sur un système multiprocesseur.  Le journal de transfert sélectionne ensuite les événements à transférer au journal central, selon les instructions données.  
  
 Vous devez enregistrer des journaux de transfert pour gérer les événements à contrôler.  Pour enregistrer des événements, les journaux doivent se substituer à la méthode <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>.  Cette méthode inclut maintenant un paramètre optionnel, `nodecount`, qui peut être configuré pour définir le nombre de processeurs du système.  \(Par défaut, il a la valeur 1.\)  
  
 Exemples d'événements que vous pouvez contrôler : <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>et <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 Dans un environnement multiprocesseur, les messages d'événement ne sont généralement pas reçus dans l'ordre.  Par conséquent, vous devez évaluer les événements en utilisant le gestionnaire d'événements dans le journal de transfert et le programmer pour déterminer les événements à communiquer au redirecteur afin de les transférer au journal central.  Pour y parvenir, vous pouvez utiliser la classe <xref:Microsoft.Build.Framework.BuildEventContext> jointe à chaque message afin d'identifier plus facilement les événements à transférer, puis passer le nom des événements à la classe <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> \(ou une de ses sous\-classes\).  Avec cette méthode, aucun autre encodage spécifique n'est nécessaire pour transférer les événements.  
  
## Spécification d'un journal de transfert  
 Après avoir compilé le journal de transfert dans un assembly, vous devez indiquer à [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de l'utiliser au cours des builds.  Pour cela, utilisez les commutateurs `/FileLogger`, `/FileLoggerParameters` et `/DistributedFileLogger` avec MSBuild.exe.  Le commutateur `/FileLogger` indique à MSBuild.exe que l'enregistreur d'événements est directement attaché. Le commutateur `/DistributedFileLogger` signifie qu'il existe un fichier journal par nœud.  Pour définir les paramètres d'un journal de transfert, utilisez le commutateur `/FileLoggerParameters`.  Pour plus d'informations sur ces commutateurs de MSBuild.exe et d'autres, consultez [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
## Journaux prenant en charge plusieurs processeurs  
 Lorsque vous construisez un projet sur un système multiprocesseur, les messages de build de chaque processeur ne sont pas automatiquement entrelacés dans une séquence unifiée.  Vous devez donc établir une priorité de regroupement des messages à l'aide de la classe <xref:Microsoft.Build.Framework.BuildEventContext> jointe à chaque message.  Pour plus d'informations sur la construction multiprocesseur, consultez [Logging in a Multi\-Processor Environment](../msbuild/logging-in-a-multi-processor-environment.md).  
  
## Voir aussi  
 [Obtention de journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Build Loggers](../msbuild/build-loggers.md)   
 [Logging in a Multi\-Processor Environment](../msbuild/logging-in-a-multi-processor-environment.md)