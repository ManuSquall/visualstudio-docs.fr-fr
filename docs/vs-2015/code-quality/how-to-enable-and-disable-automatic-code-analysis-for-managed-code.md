---
title: 'Comment : activer et désactiver l’analyse du code automatique pour le code managé | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d87cc57b31e63ae7aafa53c335df2b56f86a0409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658099"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Comment : activer et désactiver l'analyse du code automatique pour le code managé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez configurer l’analyse du code pour qu’elle s’exécute avant chaque génération d’un projet de code managé. Vous pouvez définir différentes propriétés d’analyse du code pour chaque [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Configuration.

### <a name="to-enable-or-disable-automatic-code-analysis"></a>Pour activer ou désactiver l’analyse du code automatique

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.

2. Dans la boîte de dialogue Propriétés du projet, cliquez sur **analyse du code**.

3. Spécifiez le type de build dans la **configuration** et la plateforme cible dans la **plateforme**.

4. Pour activer ou désactiver l’analyse du code automatique, activez ou désactivez la case à cocher **activer l’analyse du code sur la build (définit CODE_ANALYSIS constante)** .
