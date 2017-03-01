---
title: "Meilleures pratiques pour la sécurité dans les packages VS | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c7ceb884ad060ea45c0fd204b5611ce284d3d2af
ms.lasthandoff: 02/22/2017

---
# <a name="best-practices-for-security-in-vspackages"></a>Meilleures pratiques pour la sécurité dans les packages VS
Pour installer le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] sur votre ordinateur, vous devez exécuter dans un contexte avec les informations d’identification administratives. L’unité de base de sécurité et le déploiement d’un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] application est la [VSPackages](../../extensibility/internals/vspackages.md). Un VSPackage doit être enregistré à l’aide de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], qui nécessite également des informations d’identification administratives.  
  
 Les administrateurs ont toutes les autorisations pour écrire dans le Registre et le système de fichiers et d’exécuter du code. Vous devez disposer de ces autorisations pour développer, déployer ou installer un VSPackage.  
  
 Dès qu’il est installé, un VSPackage est entièrement fiable. En raison de ce niveau élevé d’autorisation associée à un VSPackage, il est possible d’installer accidentellement un VSPackage ayant des intentions malveillantes.  
  
 Les utilisateurs doivent s’assurer qu’ils installent VSPackages uniquement à partir de sources fiables. Sociétés développant des VSPackages doivent fortement nom et les signer, pour vous assurer que toute falsification de l’utilisateur est bloqué. Sociétés développant des VSPackages doivent examiner leurs dépendances externes, telles que les services web et d’installation à distance, d’évaluer et de corriger les problèmes de sécurité.  
  
 Pour plus d’informations, consultez les instructions de codage sécurisé pour le .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité des compléments](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [Sécurité DDEX](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)
