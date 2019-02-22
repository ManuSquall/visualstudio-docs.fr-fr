---
title: Référence des API non managées (développement Office dans Visual Studio)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 238ed42d48903d2d0ef26384245cff80785a8ebb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643702"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Référence des API non managées (développement Office dans Visual Studio)

À partir de Microsoft Office system 2007, les applications Office utilisent le [interface IManagedAddin](../vsto/imanagedaddin-interface.md) interface pour appeler un complément VSTO chargeur de composant qui est inclus avec le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Ce composant est utilisé pour aider à géré par le chargement des Compléments VSTO. Vous pouvez créer votre propre composant de chargeur de complément VSTO en implémentant cette interface.

> [!NOTE]
> Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle de compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office peu encombrantes par rapport aux compléments VSTO et de solutions, et vous pouvez les créer à l’aide de presque toutes les technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation web.

## <a name="in-this-section"></a>Dans cette section

[Interface IManagedAddin](../vsto/imanagedaddin-interface.md)

Interface COM que vous pouvez implémenter pour charger et décharger les compléments VSTO managés dans les applications Office.
