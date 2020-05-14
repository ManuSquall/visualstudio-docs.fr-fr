---
title: Meilleures pratiques pour la sécurité dans VSPackages (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4309feeed3233d2149586afb1bf4efafacb21ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709906"
---
# <a name="best-practices-for-security-in-vspackages"></a>Meilleures pratiques pour la sécurité dans VSPackages
Pour installer [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] le sur votre ordinateur, vous devez être en cours d’exécution dans un contexte avec des informations administratives. L’unité de base de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sécurité et de déploiement d’une application est le [VSPackage](../../extensibility/internals/vspackages.md). Un VSPackage doit être [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]enregistré en utilisant , ce qui nécessite également des informations administratives.

 Les administrateurs ont les autorisations complètes d’écrire au registre et au système de fichiers, et d’exécuter n’importe quel code. Vous devez avoir ces autorisations pour développer, déployer ou installer un VSPackage.

 Dès son installation, un VSPackage est entièrement fiable. En raison de ce niveau élevé d’autorisation associée à un VSPackage, il est possible d’installer par inadvertance un VSPackage qui a une intention malveillante.

 Les utilisateurs doivent s’assurer qu’ils installent VSPackages uniquement à partir de sources fiables. Les entreprises développant VSPackages devraient fortement les nommer et les signer, pour assurer à l’utilisateur que la falsification est empêchée. Les entreprises qui développent des EMBALLAGEs VS devraient examiner leurs dépendances externes, telles que les services Web et l’installation à distance, afin d’évaluer et de corriger tous les problèmes de sécurité.

 Pour plus d’informations, voir [les lignes directrices de codage sécurisée pour le cadre .NET](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Voir aussi
- [Sécurité d’ajout](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [Sécurité DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
