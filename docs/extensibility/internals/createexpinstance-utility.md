---
title: Utilitaire CreateExpInstance | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709239"
---
# <a name="createexpinstance-utility"></a>Utilitaire CreateExpInstance
Utilisez l’utilitaire **CreateExpInstance** pour créer, réinitialiser ou supprimer une instance expérimentale de Visual Studio. Vous pouvez utiliser l’instance expérimentale pour déboguer et tester des extensions Visual Studio sans modifier le produit sous-jacent.

## <a name="syntax"></a>Syntaxe

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Paramètres
 **/Create** Crée l’instance expérimentale.

 **/Reset** Supprime l’instance expérimentale, puis en crée une nouvelle.

 **/Clean** Supprime l’instance expérimentale.

 **/VSInstance** Nom du répertoire qui contient l’instance de Visual Studio de base à copier.

 **/RootSuffix** Suffixe à ajouter au nom du répertoire de l’instance expérimentale.

## <a name="remarks"></a>Notes
 Quand vous travaillez sur une extension Visual Studio, vous pouvez appuyer sur F5 pour ouvrir l’instance expérimentale par défaut et installer l’extension actuelle. Si aucune instance expérimentale n’est disponible, Visual Studio en crée une qui a les paramètres par défaut.

 L’emplacement par défaut de l’instance expérimentale dépend du numéro de version de Visual Studio. Par exemple, pour Visual Studio 2015, l’emplacement est *%LocalAppData%\Microsoft\VisualStudio\14.0Exp \\ *. Tous les fichiers de l’emplacement du répertoire sont considérés comme faisant partie de cette instance. Les instances expérimentales supplémentaires ne seront pas chargées par Visual Studio, sauf si le nom du répertoire est remplacé par l’emplacement par défaut.

 Visual Studio n’accède pas au registre système lorsqu’il ouvre l’instance expérimentale. Cela diffère des versions antérieures de Visual Studio, qui utilisaient une version expérimentale de la ruche du Registre.

 L’utilitaire **CreateExpInstance** remplace l’utilitaire **VsRegEx** .

 L’exemple suivant réinitialise l’instance expérimentale par défaut de Visual Studio :

 **CreateExpInstance.exe/Reset/VSInstance = 14.0/RootSuffix = exp**

## <a name="see-also"></a>Voir aussi
- [VSPackages](../../extensibility/internals/vspackages.md)
