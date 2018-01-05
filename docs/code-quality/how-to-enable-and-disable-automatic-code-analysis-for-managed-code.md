---
title: "Comment : activer et désactiver l’analyse du Code automatique pour le Code managé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 198047196ba6f58c69736ef67352267845047b52
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Comment : activer et désactiver l'analyse du code automatique pour le code managé
Vous pouvez configurer l’analyse du Code à exécuter avant chaque génération d’un projet de code managé. Vous pouvez définir différentes propriétés de l’analyse du Code pour chaque [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] configuration.  
  
### <a name="to-enable-or-disable-automatic-code-analysis"></a>Pour activer ou désactiver l’analyse du code automatique  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le projet, puis cliquez sur **propriétés**.  
  
2.  Dans la boîte de dialogue Propriétés du projet, cliquez sur **l’analyse du Code**.  
  
3.  Spécifiez le type de build dans **Configuration** et la plateforme cible dans **plateforme**.  
  
4.  Pour activer ou désactiver l’analyse du code automatique, activez ou désactivez le **activer analyse du Code sur la Build (définit la constante CODE_ANALYSIS)** case à cocher.