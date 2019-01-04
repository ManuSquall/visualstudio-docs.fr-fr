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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1ac4dfa9dd697993cffb527be521bd04c4c087ca
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991160"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Référence des API non managées (développement Office dans Visual Studio)
  À partir de Microsoft Office system 2007, les applications Office utilisent le [interface IManagedAddin](../vsto/imanagedaddin-interface.md) interface pour appeler un complément VSTO chargeur de composant qui est inclus avec le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Ce composant est utilisé pour aider à géré par le chargement des Compléments VSTO. Vous pouvez créer votre propre composant de chargeur de complément VSTO en implémentant cette interface.  
  
> [!NOTE]  
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle de compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office peu encombrantes par rapport aux compléments VSTO et de solutions, et vous pouvez les créer à l’aide de presque toutes les technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation web.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)  
 Interface COM que vous pouvez implémenter pour charger et décharger les compléments VSTO managés dans les applications Office.  
