---
title: Création de journaux de transfert | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 852b783129f130316de88580020e0139925ffb37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634303"
---
# <a name="create-forwarding-loggers"></a>Créer des journaux de transfert

Les journaux de transfert améliorent l’efficacité de la journalisation en vous permettant de choisir les événements que vous voulez suivre quand vous générez des projets sur un système multiprocesseur. En activant les journaux de transfert, vous pouvez empêcher des événements indésirables de submerger le journal central, de ralentir la génération et d’encombrer votre journal.

 Pour créer un journal de transfert, vous pouvez implémenter l’interface <xref:Microsoft.Build.Framework.IForwardingLogger>, puis implémenter ses méthodes manuellement ou utiliser la classe <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> et ses méthodes préconfigurées. (L’utilisation de cette classe est suffisante pour la plupart des applications.)

## <a name="register-events-and-respond-to-them"></a>Inscrire les événements et y répondre

 Un journal de transfert rassemble des informations sur les événements de génération tels qu’ils sont signalés par le moteur de génération secondaire, qui est un processus de travail créé par le processus de génération principal lors d’une génération sur un système multiprocesseur. Le journal de transfert sélectionne ensuite les événements à transférer au journal central, en fonction des instructions qui vous lui avez données.

 Vous devez inscrire les journaux de transfert pour gérer les événements que vous voulez suivre. Pour s’inscrire à des événements, les journaux doivent remplacer la méthode <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>. Cette méthode inclut maintenant un paramètre facultatif, `nodecount`, qui peut être défini sur le nombre de processeurs dans le système. (Par défaut, la valeur est 1.)

 <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> et <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> sont des exemples d’événements que vous pouvez suivre.

 Dans un environnement multiprocesseur, les messages d’événement peuvent arriver dans le désordre. Vous devez donc évaluer les événements en utilisant le gestionnaire d’événements dans le journal de transfert et le programmer de façon à déterminer quels événements passer au redirecteur pour les transférer au journal central. Pour cela, vous pouvez utiliser la classe <xref:Microsoft.Build.Framework.BuildEventContext> qui est attachée à chaque message, pour identifier les événements que vous voulez transférer, puis passer les noms des événements à la classe <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> (ou à une de ses sous-classes). Quand vous utilisez cette méthode, aucun autre code spécifique n’est nécessaire pour transférer des événements.

## <a name="specify-a-forwarding-logger"></a>Spécifier un journal de transfert

 Une fois que le journal de transfert a été compilé dans un assembly, vous devez indiquer à MSBuild de l’utiliser pendant les builds. Pour ce faire, utilisez les `-FileLogger` `-FileLoggerParameters` `-DistributedFileLogger` commutateurs, et avec *MSBuild.exe*. Le `-FileLogger` commutateur indique *MSBuild.exe* que l’enregistreur d’événements est directement attaché. Le commutateur `-DistributedFileLogger` signifie qu’il existe un fichier journal par nœud. Pour définir des paramètres sur le journal de transfert, utilisez le commutateur `-FileLoggerParameters`. Pour plus d’informations sur ces commutateurs *MSBuild.exe* , consultez [référence de la ligne de commande](../msbuild/msbuild-command-line-reference.md).

## <a name="multi-processor-aware-loggers"></a>Enregistreurs d’événements prenant en charge plusieurs processeurs

 Quand vous générez un projet sur un système multiprocesseur, les messages de génération provenant de chaque processeur ne sont pas automatiquement entrelacés dans une séquence unifiée. Vous devez donc établir une priorité de regroupement des messages avec la classe <xref:Microsoft.Build.Framework.BuildEventContext> qui est attachée à chaque message. Pour plus d’informations sur la génération de plusieurs processeurs, consultez [journalisation dans un environnement multiprocesseur](../msbuild/logging-in-a-multi-processor-environment.md).

## <a name="see-also"></a>Voir aussi

- [Obtenir des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Enregistreurs d’événements de génération](../msbuild/build-loggers.md)
- [Journalisation dans un environnement multiprocesseur](../msbuild/logging-in-a-multi-processor-environment.md)