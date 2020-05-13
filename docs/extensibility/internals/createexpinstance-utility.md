---
title: CréerExpInstance Utility (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a6b302976495e6067fad14317856cda4ac4625f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709239"
---
# <a name="createexpinstance-utility"></a>CréerExpInstance utilitaire
Utilisez l’utilitaire **CreateExpInstance** pour créer, réinitialiser ou supprimer une instance expérimentale de Visual Studio. Vous pouvez utiliser l’instance expérimentale pour déboiffer et tester les extensions Visual Studio sans changer le produit sous-jacent.

## <a name="syntax"></a>Syntaxe

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Paramètres
 **/Créer** Crée l’instance expérimentale.

 **/Reset** Supprime l’instance expérimentale, puis en crée une nouvelle.

 **/Propre** Supprime l’instance expérimentale.

 **/VSInstance** Le nom du répertoire qui contient l’instance visual studio de base à copier.

 **/RootSuffix** Le suffixe pour apprener au nom du répertoire d’instance expérimentale.

## <a name="remarks"></a>Notes
 Lorsque vous travaillez sur une extension Visual Studio, vous pouvez appuyer sur F5 pour ouvrir l’instance expérimentale par défaut et installer l’extension en cours. Si aucune instance expérimentale n’est disponible, Visual Studio en crée une qui a les paramètres par défaut.

 L’emplacement par défaut de l’instance expérimentale dépend du numéro de version Visual Studio. Par exemple, pour Visual Studio 2015, l’emplacement est *%localappdata%-Microsoft-VisualStudio-14.0Exp\\*. Tous les dossiers dans l’emplacement de l’annuaire sont considérés comme faisant partie de cette instance. Les instances expérimentales supplémentaires ne seront pas chargées par Visual Studio à moins que le nom du répertoire ne soit changé pour l’emplacement par défaut.

 Visual Studio n’a pas accès au registre du système lorsqu’il ouvre l’instance expérimentale. Cela diffère des versions antérieures de Visual Studio, qui a utilisé une version expérimentale de la ruche de registre.

 **L’utilitaire CreateExpInstance** remplace l’utilitaire **VsRegEx.**

 L’exemple suivant réinitialise l’instance expérimentale par défaut de Visual Studio :

 **CreateExpInstance.exe /Reset /VSInstance-14.0 /RootSuffix-Exp**

## <a name="see-also"></a>Voir aussi
- [VSPackages](../../extensibility/internals/vspackages.md)
