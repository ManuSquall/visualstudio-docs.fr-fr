---
title: 'Procédure : Créer un élément de travail pour une erreur de code managé'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1cb63612194148b5f3ea1f90d7c57e59fb84edbc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54941825"
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>Procédure : Créer un élément de travail pour une erreur de code managé

Vous pouvez utiliser la fonctionnalité de suivi des éléments de travail pour enregistrer l’élément de travail dans Visual Studio. Pour utiliser cette fonctionnalité, votre projet doit faire partie d’un projet Azure DevOps dans [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].

## <a name="to-create-a-work-item-for-managed-code-defect"></a>Pour créer un élément de travail pour l’erreur de code managé

1. Dans le **analyse du Code** fenêtre, sélectionnez l’avertissement.

2. Choisissez **Actions**, puis choisissez **créer un élément de travail** et choisissez le type d’élément de travail à créer.

     Un nouvel élément de travail est créé pour vous permettent de spécifier les informations sur les erreurs.

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>Pour créer un élément de travail pour plusieurs erreurs de code managé

1. Dans le **liste d’erreurs**, sélectionnez plusieurs avertissements, puis cliquez sur les avertissements.

2. Pointez sur **créer un élément de travail** et cliquez sur le type d’élément de travail à créer.

     Un seul élément de travail est créé pour tous les avertissements sélectionnés pour vous permettent de spécifier les informations sur les bogues.