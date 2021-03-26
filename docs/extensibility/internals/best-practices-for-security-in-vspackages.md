---
title: Meilleures pratiques pour la sécurité dans les VSPackages | Microsoft Docs
description: Découvrez les meilleures pratiques en matière de sécurité dans un VSPackage, l’unité de base de sécurité et le déploiement d’une application Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cca66d6c1fce0deb8103a7d626c16a4e81bc7b5f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086207"
---
# <a name="best-practices-for-security-in-vspackages"></a>Meilleures pratiques pour la sécurité dans les VSPackages
Pour installer le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] sur votre ordinateur, vous devez être en cours d’exécution dans un contexte avec des informations d’identification d’administration. Le VSPackage est l’unité de base de sécurité et de déploiement d’une [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] application. [](../../extensibility/internals/vspackages.md) Un VSPackage doit être inscrit à l’aide de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , qui requiert également des informations d’identification d’administration.

 Les administrateurs ont des autorisations complètes pour écrire dans le registre et le système de fichiers, et pour exécuter du code. Vous devez disposer des autorisations suivantes pour développer, déployer ou installer un VSPackage.

 Dès qu’il est installé, un VSPackage est entièrement fiable. En raison de ce niveau élevé d’autorisation associé à un VSPackage, il est possible d’installer par inadvertance un VSPackage qui a un but malveillant.

 Les utilisateurs doivent s’assurer qu’ils installent les VSPackages uniquement à partir de sources approuvées. Les entreprises développant des VSPackages doivent les nommer et les signer de manière à ce que l’utilisateur ne puisse pas le falsifier. Les entreprises développant des VSPackages doivent examiner leurs dépendances externes, telles que les services Web et l’installation à distance, pour évaluer et corriger les problèmes de sécurité.

 Pour plus d’informations, consultez [recommandations en matière de codage sécurisé pour le .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Voir aussi
- [Sécurité des compléments](/previous-versions/1326zbk3(v=vs.140))
- [Sécurité de DDEX](/previous-versions/bb163703(v=vs.140))