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
ms.openlocfilehash: 97388073d63b25bb17a7f49f4e2c5fb96bf2f572
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767895"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Référence des API non managées (développement Office dans Visual Studio)
  À compter de Microsoft Office system 2007, les applications Office utilisent le [interface IManagedAddin](../vsto/imanagedaddin-interface.md) interface pour appeler un composant de chargeur du complément VSTO qui est inclus dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Ce composant vise à faciliter le chargement des compléments VSTO managés. Vous pouvez créer votre propre composant de chargeur de complément VSTO en implémentant cette interface.  
  
> [!NOTE]  
>  Vous souhaitez développer des solutions qui étendent l’expérience Office sur [plusieurs plateformes](https://dev.office.com/add-in-availability)? Découvrez le nouvel [modèle des compléments Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Compléments Office ont un faible encombrement mémoire par rapport aux compléments VSTO et les solutions, et vous pouvez les créer à l’aide de presque n’importe quel web technologies, telles que HTML5, JavaScript, CSS3 et XML de programmation.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)  
 Interface COM que vous pouvez implémenter pour charger et décharger les compléments VSTO managés dans les applications Office.  
  
  