---
title: "Meilleures pratiques pour la sécurité dans les VSPackages | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 71f06fdd67e4f1789637c2d935f0d25a06eb9863
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-security-in-vspackages"></a>Meilleures pratiques pour la sécurité dans les VSPackages
Pour installer le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] sur votre ordinateur, vous devez être en cours d’exécution dans un contexte avec les informations d’identification d’administration. L’unité de base de la sécurité et le déploiement d’un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] application est la [VSPackages](../../extensibility/internals/vspackages.md). Un VSPackage doit être inscrit à l’aide de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ce qui nécessite également des informations d’identification d’administration.  
  
 Les administrateurs disposent des autorisations complètes à écrire dans le Registre et le système de fichiers et d’exécuter du code. Vous devez disposer de ces autorisations pour développer, déployer ou installez un VSPackage.  
  
 Dès qu’il est installé, un VSPackage est entièrement fiable. En raison de ce niveau d’autorisation associée à un VSPackage élevé, il est possible par inadvertance installer un VSPackage qui a un but malveillant.  
  
 Les utilisateurs doivent s’assurer qu’ils installent des VSPackages uniquement à partir de sources fiables. Sociétés développant des VSPackages doivent fortement nom et les signer, afin de garantir l’utilisateur que la falsification est bloqué. Développement de VSPackages des sociétés doivent examiner leurs dépendances externes, tels que les services web et d’installation à distance, pour évaluer et corriger les problèmes de sécurité.  
  
 Pour plus d’informations, consultez les instructions de codage sécurisé pour le .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du complément](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [Sécurité DDEX](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)