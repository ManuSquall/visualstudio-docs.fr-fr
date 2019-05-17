---
title: Meilleures pratiques pour la sécurité dans VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 940644cd3950c38c6383371c1844b54b328acd0c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697267"
---
# <a name="best-practices-for-security-in-vspackages"></a>Bonnes pratiques de sécurité dans VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pour installer le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] sur votre ordinateur, vous devez être en cours d’exécution dans un contexte avec les informations d’identification d’administration. L’unité de base de sécurité et le déploiement d’un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] application est la [VSPackages](../../extensibility/internals/vspackages.md). Un VSPackage doit être inscrit à l’aide de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], ce qui nécessite également des informations d’identification d’administration.  
  
 Les administrateurs ont des autorisations complètes pour écrire dans le Registre et le système de fichiers et d’exécuter du code. Vous devez disposer de ces autorisations pour développer, déployer ou installer un VSPackage.  
  
 Dès qu’il est installé, un VSPackage est entièrement fiable. En raison de ce niveau élevé de l’autorisation associée à un VSPackage, il est possible d’installer par inadvertance un VSPackage ayant un but malveillant.  
  
 Les utilisateurs doivent s’assurer qu’ils installent VSPackages uniquement à partir de sources approuvées. Sociétés de développement de VSPackages doivent fortement nommez et signez-les, afin de garantir l’utilisateur que falsification est empêchée. Sociétés de développement de VSPackages doivent examiner leurs dépendances externes, telles que les services web et l’installation à distance, à évaluer et corriger les problèmes de sécurité.  
  
 Pour plus d’informations, consultez les instructions de codage sécurisé pour le .NET Framework ([https://msdn.microsoft.com/library/d55zzx87.aspx](https://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité des compléments](https://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [Sécurité DDEX](https://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
