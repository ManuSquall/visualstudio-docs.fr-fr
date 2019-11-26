---
title: VSPackages et infrastructure de package managée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 84fb41bfc80415535ca41d6b1a8c9dcf47124c7a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298232"
---
# <a name="vspackages-and-the-managed-package-framework"></a>VSPackages et infrastructure de package gérée
Vous pouvez réduire le temps de développement en créant un VSPackage avec les classes Managed package Framework (MPF) au lieu d’utiliser des classes de COM Interop.  
  
 Il existe deux façons de créer un VSPackage géré :  
  
- Utiliser le modèle de projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] package  
  
     Pour plus d’informations, consultez [procédure pas à pas : création d’une commande de menu à l’aide du modèle de package Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
- Créer votre VSPackage sans le modèle de projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] package  
  
     Par exemple, vous pouvez copier un exemple de VSPackage et modifier les GUID et les noms. 
  
## <a name="in-this-section"></a>Dans cette section  
 [Classes MPF (Managed Package Framework)](../misc/managed-package-framework-classes.md)  
 Décrit et répertorie les espaces de noms de classe MPF et les fichiers DLL.  
  
## <a name="related-sections"></a>Sections connexes  
 [Procédure pas à pas : création d’une commande de menu à l’aide du modèle de package Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Explique comment créer un VSPackage managé.  
  
 [VSPackages gérés](../misc/managed-vspackages.md)  
 Introduit les aspects des VSPackages qui s’appliquent au code managé.