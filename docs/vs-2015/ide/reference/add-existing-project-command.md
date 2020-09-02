---
title: Ajouter un projet existant, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 73d8e54938659920227b3614046b8a8f933023ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670215"
---
# <a name="add-existing-project-command"></a>Ajouter un projet existant, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ajoute un projet existant à la solution actuelle.

## <a name="syntax"></a>Syntaxe

```
File.AddExistingProject filename
```

## <a name="arguments"></a>Arguments
 `filename` Facultatif. Chemin complet et nom (extension comprise) du projet à ajouter à la solution.

 Si l’argument `filename` comprend des espaces, il doit être placé entre guillemets.

 Si aucun nom de fichier n’est spécifié, la commande ouvre la boîte de dialogue Fichier pour que l’utilisateur puisse sélectionner un projet.

## <a name="remarks"></a>Notes
 La saisie semi-automatique tente de deviner le chemin et le nom de fichier à mesure que vous tapez.

## <a name="example"></a>Exemple
 Cet exemple ajoute le projet [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (TestProject1) à la solution actuelle.

```
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Voir aussi
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md) [fenêtre commande](../../ide/reference/command-window.md) [Rechercher/zone de commande](../../ide/find-command-box.md) [alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
