---
title: -InstallVSTemplates (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /InstallVSTemplates switch
- /InstallVSTemplates Devenv switch
- InstallVSTemplates switch
ms.assetid: 1fb466f6-7955-4535-a840-d93eb8aaa492
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2f019af21beba231a5f135c49fb00dcb463e110
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671010"
---
# <a name="installvstemplates-devenvexe"></a>/InstallVSTemplates (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Inscrit les modèles de projet ou d’élément qui se trouvent dans *\<Visual Studio installation path>* \Common7\IDE\ProjectTemplates\ ou *\<Visual Studio installation path>* \Common7\IDE\ItemTemplates\ afin qu’ils soient accessibles par le biais des boîtes de dialogue **nouveau projet** et **Ajouter un nouvel élément** .

> [!WARNING]
> Ce commutateur est pris en charge uniquement pour le développement des partenaires Visual Studio, il n’est pas disponible dans les éditions Express. Vous devez exécuter devenv en tant qu’administrateur pour pouvoir utiliser les commutateurs [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) et [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md). Pour plus d’informations, consultez [Autorisations de l’utilisateur](../../ide/user-permissions-and-visual-studio.md).

## <a name="syntax"></a>Syntaxe

```
devenv.exe /InstallVSTemplates
```

## <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi
 [Commutateurs de ligne de commande devenv](../../ide/reference/devenv-command-line-switches.md)
