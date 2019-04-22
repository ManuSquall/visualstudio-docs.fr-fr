---
title: Configuration des cibles et des tâches | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d3ed6456ecf4ca226368338078247a10d80cee3
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59660591"
---
# <a name="configuring-targets-and-tasks"></a>Configuration des cibles et des tâches
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez configurer des cibles et des tâches MSBuild pour qu’elles s’exécutent hors processus avec MSBuild. Vous pouvez ainsi cibler des contextes différents de celui dans lequel vous vous trouvez. Par exemple, vous pouvez cibler une application .NET Framework 2.0 32 bits alors que l’ordinateur de développement s’exécute sur un système d’exploitation 64 bits avec le .NET Framework 4.5. Vous pouvez également cibler des ordinateurs qui exécutent le .NET Framework 4 ou version antérieure. La combinaison d’un système 32 et 64 bits et de la version spécifique du .NET Framework est appelée *contexte cible*.  
  
## <a name="installation"></a>Installation  
 Les versions 4.5 et 4.5.1 du .NET Framework remplacent le common language runtime (CLR), les cibles, les tâches et les outils du .NET Framework 4 sans les renommer. Le .NET Framework 4.5.1 est installé en même temps que [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].  
  
 Si vous souhaitez installer MSBuild séparément de Visual Studio, vous pouvez télécharger le package d’installation à partir de la page de [téléchargement de MSBuild](http://go.microsoft.com/fwlink/?LinkId=309745). Vous devez également installer les versions du .NET Framework que vous souhaitez utiliser.  
  
## <a name="targets-and-tasks"></a>Cibles et tâches  
 MSBuild exécute certaines des tâches de génération hors processus pour cibler un ensemble plus important de contextes.  Par exemple, un MSBuild 32 bits peut exécuter une tâche de génération dans un processus 64 bits pour cibler un ordinateur 64 bits. Pour cela, utilisez les arguments `UsingTask` et les paramètres `Task`. Les cibles installées par le .NET Framework 4.5 définissent ces paramètres et ces arguments, et aucune modification n’est nécessaire pour générer des applications adaptées aux différents contextes cible.  
  
 Si vous souhaitez créer votre propre contexte cible, vous devez définir correctement ces paramètres et ces arguments. Pour obtenir des exemples, reportez-vous au fichier Microsoft.Common.targets du .NET Framework 4.5 et au fichier Microsoft.Common.Tasks.  Pour plus d’informations sur la façon de créer une tâche personnalisée pouvant fonctionner avec plusieurs contextes cibles, ou sur la façon de modifier des tâches existantes, consultez [Guide pratique pour Configurer les cibles et tâches](../msbuild/how-to-configure-targets-and-tasks.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Multiciblage](../msbuild/msbuild-multitargeting-overview.md)
