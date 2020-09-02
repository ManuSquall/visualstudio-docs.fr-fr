---
title: 'Comment : supprimer des avertissements d’analyse du code pour du code généré | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52caadd7f4dd9349eccb80a366a1458212aba5ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646276"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Comment : supprimer les avertissements d'analyse du code pour du code généré
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les compilateurs de code managé génèrent souvent du code qui est ajouté à un projet pour faciliter le développement rapide de code. En outre, les développeurs utilisent souvent des outils tiers pour développer rapidement des applications. Ces outils génèrent également du code qui est ajouté au projet.

 Vous pouvez consulter les violations de règle découvertes par l’analyse du code dans le code généré. Toutefois, vous ne voudrez peut-être pas les afficher si vous ne pouvez pas afficher et gérer le code qui contient la violation.

 La case à cocher **Supprimer les résultats du code généré** sur la page de propriétés analyse du code d’un projet vous permet de choisir si vous souhaitez consulter les avertissements d’analyse du code générés par un outil tiers.

> [!NOTE]
> Cette option ne supprime pas les erreurs et les avertissements d’analyse du code générés lorsque les erreurs et les avertissements s’affichent dans les formulaires et les modèles. Vous pouvez afficher et gérer le code source pour un formulaire ou un modèle.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Pour supprimer des avertissements pour le code généré dans un projet

1. Cliquez avec le bouton droit sur le projet dans Explorateur de solutions, puis cliquez sur **Propriétés**.

2. Cliquez sur **Analyse du code**.

3. Activez la case à cocher **Supprimer les résultats du code généré** .
