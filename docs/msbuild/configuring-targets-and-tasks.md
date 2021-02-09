---
title: Configuration des cibles et des tâches | Microsoft Docs
description: Configurer des cibles et des tâches MSBuild pour qu’elles s’exécutent hors processus avec MSBuild afin que vous puissiez cibler des contextes qui diffèrent de celui sur lequel vous exécutez.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5548478e5404c69acc92d7ca7dc4deb6a2e29fdf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922540"
---
# <a name="configure-targets-and-tasks"></a>Configurer les cibles et les tâches

Vous pouvez configurer des cibles et des tâches MSBuild pour qu’elles s’exécutent hors processus avec MSBuild. Vous pouvez ainsi cibler des contextes différents de celui dans lequel vous vous trouvez. Par exemple, vous pouvez cibler une application .NET Framework 2.0 32 bits alors que l’ordinateur de développement s’exécute sur un système d’exploitation 64 bits avec le .NET Framework 4.5. Vous pouvez également cibler des ordinateurs qui exécutent le .NET Framework 4 ou version antérieure. La combinaison d’un système 32 et 64 bits et de la version spécifique du .NET Framework est appelée *contexte cible*.

## <a name="installation"></a>Installation

  Si vous souhaitez installer MSBuild séparément de Visual Studio, vous pouvez télécharger le package d’installation à partir de la page de [téléchargement de MSBuild](https://www.microsoft.com/download/details.aspx?id=40760). Vous devez également installer les versions du .NET Framework que vous souhaitez utiliser.

## <a name="targets-and-tasks"></a>Cibles et tâches

 MSBuild exécute certaines des tâches de génération hors processus pour cibler un ensemble plus important de contextes.  Par exemple, un MSBuild 32 bits peut exécuter une tâche de génération dans un processus 64 bits pour cibler un ordinateur 64 bits. Pour cela, utilisez les arguments `UsingTask` et les paramètres `Task`. Les cibles installées par le .NET Framework 4.5 définissent ces paramètres et ces arguments, et aucune modification n’est nécessaire pour générer des applications adaptées aux différents contextes cible.

 Si vous souhaitez créer votre propre contexte cible, vous devez définir correctement ces paramètres et ces arguments. Pour obtenir des exemples, examinez les fichiers *Microsoft.Common.targets* et *Microsoft.Common.Tasks* de .NET Framework 4.5.  Pour plus d’informations sur la création d’une tâche personnalisée pouvant fonctionner avec plusieurs contextes cibles, ou sur la modification de tâches existantes, consultez [Guide pratique pour configurer les cibles et les tâches](../msbuild/how-to-configure-targets-and-tasks.md).

## <a name="see-also"></a>Voir aussi

- [Multi-ciblage](../msbuild/msbuild-multitargeting-overview.md)
