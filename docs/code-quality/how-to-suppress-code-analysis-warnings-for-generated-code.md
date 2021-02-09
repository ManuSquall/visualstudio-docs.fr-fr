---
title: Supprimer les violations d’analyse du code pour le code généré
ms.date: 05/13/2019
description: Découvrez comment supprimer les avertissements d’analyse du code pour le code généré. Consultez Comment empêcher Visual Studio d’afficher les avertissements d’analyse héritée sur le code généré.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a149511b447f1f21d180eaf526ebc3d991c95997
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859942"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Comment : supprimer des avertissements d’analyse du code pour du code généré

Le code généré comprend du code qui est ajouté à votre projet par des compilateurs de code managé ou des outils tiers. Vous pouvez consulter les violations de règle découvertes par l’analyse du code dans le code généré. Toutefois, étant donné que vous ne pouvez pas afficher et gérer le code qui contient les violations, vous ne voudrez peut-être pas les afficher.

La case à cocher **Supprimer les résultats du code généré** sur la page de propriétés analyse du code d’un projet vous permet de choisir d’afficher ou non les avertissements d’analyse du code générés par un outil tiers.

> [!NOTE]
> Cette option ne supprime pas les erreurs d'analyse du code et les avertissements du code généré qui apparaissent dans les formulaires et les modèles. Vous pouvez afficher et gérer le code source pour un formulaire ou un modèle.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Pour supprimer des avertissements pour le code généré dans un projet

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.

2. Choisissez l’onglet **analyse du code** .

3. Activez la case à cocher **Supprimer les résultats du code généré** .

> [!IMPORTANT]
> Vous pouvez uniquement supprimer les avertissements de l’analyse héritée. La page de propriétés avec le paramètre est dépréciée et sera supprimée dans une version future du produit. Actuellement, vous ne pouvez pas supprimer les avertissements d’analyse du code des [analyseurs](roslyn-analyzers-overview.md).
