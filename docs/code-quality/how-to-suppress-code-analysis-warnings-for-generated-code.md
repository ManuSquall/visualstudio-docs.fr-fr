---
title: Supprimer les violations de l’analyse du Code pour le Code généré
ms.date: 05/13/2019
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a7990f5e9fa1893d8813b1307ab6a0a7fee46be
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65613572"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Procédure : Supprimer les avertissements d’analyse du code pour le code généré

Code généré inclut le code qui est ajouté à votre projet par les compilateurs de code managé ou des outils tiers. Vous souhaiterez peut-être consulter les violations de règle que l’analyse du code détecte dans le code généré. Toutefois, étant donné que vous ne peut pas afficher et gérer le code qui contient les violations, vous souhaiterez pas les voir.

Le **supprimer les résultats du code généré** case à cocher sur la page propriété analyse du code d’un projet vous permet de sélectionner s’il faut afficher des avertissements d’analyse du code généré par un outil tiers de code.

> [!NOTE]
> Cette option ne supprime pas les erreurs d'analyse du code et les avertissements du code généré qui apparaissent dans les formulaires et les modèles. Vous pouvez afficher et gérer le code source pour un formulaire ou un modèle.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Pour supprimer des avertissements pour du code généré dans un projet

1. Cliquez sur le projet dans **l’Explorateur de solutions** puis cliquez sur **propriétés**.

2. Choisissez le **analyse du Code** onglet.

3. Sélectionnez le **supprimer les résultats du code généré** case à cocher.

> [!NOTE]
> Vous pouvez uniquement supprimer des avertissements d’analyse statique du code. Actuellement, vous ne pouvez pas supprimer les avertissements d’analyse du code à partir de [analyseurs](roslyn-analyzers-overview.md).