---
title: Meilleures pratiques pour la sécurité dans les VSPackages | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697267"
---
# <a name="best-practices-for-security-in-vspackages"></a>Bonnes pratiques de sécurité dans VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pour installer le [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] sur votre ordinateur, vous devez être en cours d’exécution dans un contexte avec des informations d’identification d’administration. L’unité de base de sécurité et le déploiement d’une [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] application sont les [VSPackages](../../extensibility/internals/vspackages.md). Un VSPackage doit être inscrit à l’aide de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , qui requiert également des informations d’identification d’administration.  
  
 Les administrateurs ont des autorisations complètes pour écrire dans le registre et le système de fichiers, et pour exécuter du code. Vous devez disposer des autorisations suivantes pour développer, déployer ou installer un VSPackage.  
  
 Dès qu’il est installé, un VSPackage est entièrement fiable. En raison de ce niveau élevé d’autorisation associé à un VSPackage, il est possible d’installer par inadvertance un VSPackage qui a un but malveillant.  
  
 Les utilisateurs doivent s’assurer qu’ils installent les VSPackages uniquement à partir de sources approuvées. Les entreprises développant des VSPackages doivent les nommer et les signer de manière à ce que l’utilisateur ne puisse pas le falsifier. Les entreprises développant des VSPackages doivent examiner leurs dépendances externes, telles que les services Web et l’installation à distance, pour évaluer et corriger les problèmes de sécurité.  
  
 Pour plus d’informations, consultez recommandations en matière de codage sécurisé pour le .NET Framework ( [https://msdn.microsoft.com/library/d55zzx87.aspx](https://msdn.microsoft.com/library/d55zzx87.aspx) ).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité des compléments](https://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [Sécurité de DDEX](https://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
