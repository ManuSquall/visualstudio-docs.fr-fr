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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed03833b6c109ca78feb86c1cfe41fa453022c66
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341914"
---
# <a name="createexpinstance-utility"></a>Utilitaire CreateExpInstance
Utilisez le **CreateExpInstance** utilitaire pour créer, réinitialiser ou supprimer une instance expérimentale de Visual Studio. Vous pouvez utiliser l’instance expérimentale pour déboguer et tester des extensions Visual Studio sans modifier le produit sous-jacent.

## <a name="syntax"></a>Syntaxe

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Paramètres
 **/ Création** crée l’instance expérimentale.

 **/ Réinitialisation** supprime l’instance expérimentale et crée un nouveau.

 **/ Nettoyage** supprime l’instance expérimentale.

 **/ VSInstance** le nom du répertoire qui contient l’instance de Visual Studio de base à copier.

 **/ RootSuffix** le suffixe à ajouter au nom du répertoire d’instance expérimentale.

## <a name="remarks"></a>Notes
 Lorsque vous travaillez sur une extension Visual Studio, vous pouvez appuyer sur F5 pour ouvrir l’instance expérimentale par défaut et installer l’extension actuelle. Si aucune instance expérimentale n’est disponible, Visual Studio crée un objet qui contient les paramètres par défaut.

 L’emplacement par défaut de l’instance expérimentale varie selon le numéro de version de Visual Studio. Par exemple, pour Visual Studio 2015, l’emplacement est *%localappdata%\Microsoft\VisualStudio\14.0Exp\\* . Tous les fichiers dans l’emplacement du répertoire sont considérées comme partie de cette instance. Toutes les instances expérimentales supplémentaires ne seront pas chargés par Visual Studio, sauf si le nom du répertoire est modifié à l’emplacement par défaut.

 Visual Studio n’accède pas au Registre système lorsqu’il ouvre l’instance expérimentale. Cela diffère des versions antérieures de Visual Studio, qui ont utilisé une version expérimentale de la ruche du Registre.

 Le **CreateExpInstance** utilitaire remplace le **VsRegEx** utilitaire.

 L’exemple suivant réinitialise l’instance expérimentale de la valeur par défaut de Visual Studio :

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>Voir aussi
- [VSPackages](../../extensibility/internals/vspackages.md)