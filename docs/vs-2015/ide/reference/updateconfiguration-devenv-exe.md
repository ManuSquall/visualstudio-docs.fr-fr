---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50773821b328ea81381744bc6f32b3907cd1c5bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657917"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Notifie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour qu’il fusionne les packages [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sur le système et vérifie si des modifications ont été apportées au cache MEF.

## <a name="syntax"></a>Syntaxe

```
devenv /updateconfiguration
```

## <a name="remarks"></a>Notes
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] exécute cette commande automatiquement quand vous installez un package VSIX. Vous devez exécuter `devenv.exe /updateconfiguration` après la mise à jour corrective de vos fichiers pour que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mette à jour le cache MEF. Cela vous permet d’évaluer si votre correctif est adapté.

## <a name="example"></a>Exemple
 La ligne de commande suivante permet à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] de fusionner les packages [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sur le système et de vérifier si des modifications ont été apportées au cache MEF.

```
Devenv.exe /updateconfiguration
```

## <a name="see-also"></a>Voir aussi
 [Personnalisation des paramètres de développement dans](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) les [commutateurs de ligne de commande devenv](../../ide/reference/devenv-command-line-switches.md) de Visual Studio
