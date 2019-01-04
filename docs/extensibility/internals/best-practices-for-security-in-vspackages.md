---
title: Meilleures pratiques pour la sécurité dans VSPackages | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 93ff8f6cd9423212a64404b55b38751d095b260f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913384"
---
# <a name="best-practices-for-security-in-vspackages"></a>Meilleures pratiques pour la sécurité dans VSPackages
Pour installer le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] sur votre ordinateur, vous devez être en cours d’exécution dans un contexte avec les informations d’identification d’administration. L’unité de base de sécurité et le déploiement d’un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] application est la [VSPackage](../../extensibility/internals/vspackages.md). Un VSPackage doit être inscrit à l’aide de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ce qui nécessite également des informations d’identification d’administration.  
  
 Les administrateurs ont des autorisations complètes pour écrire dans le Registre et le système de fichiers et d’exécuter du code. Vous devez disposer de ces autorisations pour développer, déployer ou installer un VSPackage.  
  
 Dès qu’il est installé, un VSPackage est entièrement fiable. En raison de ce niveau élevé de l’autorisation associée à un VSPackage, il est possible d’installer par inadvertance un VSPackage ayant un but malveillant.  
  
 Les utilisateurs doivent s’assurer qu’ils installent VSPackages uniquement à partir de sources approuvées. Sociétés de développement de VSPackages doivent fortement nommez et signez-les, afin de garantir l’utilisateur que falsification est empêchée. Sociétés de développement de VSPackages doivent examiner leurs dépendances externes, telles que les services web et l’installation à distance, à évaluer et corriger les problèmes de sécurité.  
  
 Pour plus d’informations, consultez [sécurisé en matière de codage pour le .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité des compléments](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [Sécurité DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)