---
title: Meilleures pratiques pour la sécurité dans VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5b3b86736a5425640c1a87df6a3e2c6e6cec0c5
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513346"
---
# <a name="best-practices-for-security-in-vspackages"></a>Meilleures pratiques pour la sécurité dans VSPackages
Pour installer le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] sur votre ordinateur, vous devez être en cours d’exécution dans un contexte avec les informations d’identification d’administration. L’unité de base de sécurité et le déploiement d’un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] application est la [VSPackage](../../extensibility/internals/vspackages.md). Un VSPackage doit être inscrit à l’aide de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ce qui nécessite également des informations d’identification d’administration.  
  
 Les administrateurs ont des autorisations complètes pour écrire dans le Registre et le système de fichiers et d’exécuter du code. Vous devez disposer de ces autorisations pour développer, déployer ou installer un VSPackage.  
  
 Dès qu’il est installé, un VSPackage est entièrement fiable. En raison de ce niveau élevé de l’autorisation associée à un VSPackage, il est possible d’installer par inadvertance un VSPackage ayant un but malveillant.  
  
 Les utilisateurs doivent s’assurer qu’ils installent VSPackages uniquement à partir de sources approuvées. Sociétés de développement de VSPackages doivent fortement nommez et signez-les, afin de garantir l’utilisateur que falsification est empêchée. Sociétés de développement de VSPackages doivent examiner leurs dépendances externes, telles que les services web et l’installation à distance, à évaluer et corriger les problèmes de sécurité.  
  
 Pour plus d’informations, consultez [sécurisé en matière de codage pour le .NET Framework](http://msdn.microsoft.com/library/d55zzx87.aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité des compléments](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [Sécurité DDEX](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)