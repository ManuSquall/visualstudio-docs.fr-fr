---
title: Enregistrer la sortie de la fenêtre Commande, commande | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57a1393c6db4da7b652490cbf9d352ad7b4455cd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="log-command-window-output-command"></a>Enregistrer la sortie de la fenêtre de commande, commande
Copie toutes les entrées et sorties de la fenêtre **Commande** dans un fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Facultative. Nom du fichier journal. Par défaut, le fichier est créé dans le dossier du profil de l’utilisateur. Si le nom de fichier existe déjà, le journal est ajouté à la fin du fichier existant. Si aucun fichier n’est spécifié, le dernier fichier spécifié est utilisé. Si aucun fichier n’a été spécifié précédemment, le fichier journal cmdline.log est créé par défaut.  
  
> [!TIP]
>  Pour modifier l’emplacement d’enregistrement du fichier journal, entrez le chemin complet du fichier, en l’entourant de guillemets s’il comporte des espaces.  
  
## <a name="switches"></a>Commutateurs  
 /on  
 Facultative. Démarre le journal pour la fenêtre **Commande** dans le fichier spécifié et ajoute les nouvelles informations à la fin de ce fichier.  
  
 /off  
 Facultative. Arrête le journal pour la fenêtre **Commande**.  
  
 /overwrite  
 Facultative. Si le fichier spécifié dans l’argument `filename` est identique à un fichier existant, celui-ci est remplacé.  
  
## <a name="remarks"></a>Notes  
 Si aucun fichier n’est spécifié, le fichier cmdline.log est créé par défaut. L’alias par défaut de cette commande est Log.  
  
## <a name="examples"></a>Exemples  
 Cet exemple crée le fichier journal cmdlog, puis démarre l’enregistrement des commandes.  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 Cet exemple arrête l’enregistrement des commandes.  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 Cet exemple reprend l’enregistrement des commandes dans le dernier fichier journal utilisé.  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)