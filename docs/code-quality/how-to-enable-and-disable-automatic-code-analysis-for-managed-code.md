---
title: "Comment : activer et désactiver l'analyse du code automatique pour le code managé"
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3113143b07ccb6f765cd0cf1735b34be6e952c72
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47443543"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Comment : activer et désactiver l’analyse du code automatique pour le code managé

Vous pouvez configurer l’analyse du code à exécuter après chaque génération d’un projet de code managé. Vous pouvez définir des propriétés d’analyse pour chaque configuration de build de code différents, par exemple, debug et release.

## <a name="to-enable-or-disable-automatic-code-analysis"></a>Pour activer ou désactiver l’analyse du code automatique

1. Dans **l’Explorateur de solutions**, cliquez sur le projet, puis choisissez **propriétés**.

1. Dans la boîte de dialogue Propriétés du projet, choisissez le **analyse du Code** onglet.

1. Spécifiez le type de build dans **Configuration** et la plateforme cible dans **plateforme**.

1. Pour activer ou désactiver l’analyse du code automatique, activez ou désactivez le **activer l’analyse du Code sur la Build** case à cocher.

> [!NOTE]
> Le **activer l’analyse du Code sur la Build** case à cocher affecte uniquement l’analyse statique du code. Cela n’affecte pas [analyseurs de code Roslyn](roslyn-analyzers-overview.md), qui s’exécutent toujours à la conférence build si vous avez installé les comme package NuGet. Si vous souhaitez effacer les erreurs de l’Analyseur de la **liste d’erreurs**, vous pouvez supprimer toutes les violations actuelles en choisissant **analyser** > **exécuter l’analyse du Code et supprimer Active Problèmes** sur la barre de menus. Pour plus d’informations, consultez [supprimer violations](use-roslyn-analyzers.md#suppress-violations).
