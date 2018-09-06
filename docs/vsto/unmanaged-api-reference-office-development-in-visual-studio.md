---
title: Référence des API non managées (développement Office dans Visual Studio)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 9b0f48ea5997c2c8c2dd7d90eebde8322fad8a7a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671088"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Référence des API non managées (développement Office dans Visual Studio)
  À partir de Microsoft Office system 2007, les applications Office utilisent le [interface IManagedAddin](../vsto/imanagedaddin-interface.md) interface pour appeler un complément VSTO chargeur de composant qui est inclus avec le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Ce composant est utilisé pour aider à géré par le chargement des Compléments VSTO. Vous pouvez créer votre propre composant de chargeur de complément VSTO en implémentant cette interface.  
  
> [!NOTE]  
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle de compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office peu encombrantes par rapport aux compléments VSTO et de solutions, et vous pouvez les créer à l’aide de presque toutes les technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation web.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)  
 Interface COM que vous pouvez implémenter pour charger et décharger les compléments VSTO managés dans les applications Office.  
  
  