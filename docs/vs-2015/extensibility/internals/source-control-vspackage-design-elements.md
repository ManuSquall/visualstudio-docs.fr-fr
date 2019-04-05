---
title: Éléments de conception de VSPackage de contrôle source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 06cd4523f91c341029140764b31fbd0ee262d551
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950857"
---
# <a name="source-control-vspackage-design-elements"></a>Éléments de conception de VSPackage de contrôle de source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les rubriques de cette section décrivent la structure le VSPackage doit implémenter pour l’intégration approfondie de contrôle de code source. Il répertorie également les interfaces et les services que la source de contrôle VSPackage peuvent implémenter, et utiliser les interfaces et les services le VSPackage de contrôle de code source à partir d’autres [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] composants pour prendre en charge de sa source de contrôlent le modèle et les fonctionnalités.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Structure VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Définit la structure de contrôle de source de package Visual Studio.  
  
 [Interfaces et services associés](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Répertorie les interfaces d’associées au package de contrôle de source et de services.  
  
 [Services fournis](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Décrit le service de contrôle de code source fourni par le VSPackage de contrôle de code source.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Explique comment créer un contrôle de code source VSPackage qui non seulement fournit des fonctionnalités de contrôle de code source, mais peut être utilisé pour personnaliser le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l’interface utilisateur de contrôle de code source.
