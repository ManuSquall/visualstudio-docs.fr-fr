---
title: "Shell, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.shell"
helpviewer_keywords: 
  - "fichiers .exe"
  - "fichiers exe"
  - "exécutables, démarrer à partir de Visual Studio"
  - "Shell (commande)"
  - "Shell, lancer des fichiers exe"
  - "Tools.Shell (commande)"
  - "Visual Studio, exécutables à partir de"
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Shell, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lance les programmes exécutables à partir de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Syntaxe  
  
```  
Tools.Shell [/command] [/output] [/dir:folder] path [args]  
```  
  
## Arguments  
 `path`  
 Obligatoire.  Chemin d'accès et nom du fichier à exécuter ou du document à ouvrir.  Un chemin d'accès complet est requis si le fichier spécifié ne se trouve pas dans l'un des répertoires figurant dans la variable d'environnement PATH.  
  
 `args`  
 Facultatif.  Arguments passés au programme appelé, s'il y a lieu.  
  
## Commutateurs  
 \/commandwindow \[ou\] \/command \[ou\] \/c \[ou\] \/cmd  
 Facultatif.  Spécifie que la sortie pour l'exécutable doit s'afficher dans la fenêtre **Commande**.  
  
 \/dir:`folder` \[ou\] \/d: `folder`  
 Facultatif.  Spécifie le répertoire de travail à définir lorsque le programme est exécuté.  
  
 \/outputwindow \[ou\] \/output \[ou\] \/out \[ou\] \/o  
 Facultatif.  Spécifie que la sortie pour l'exécutable doit s'afficher dans la fenêtre **Sortie**.  
  
## Notes  
 Les commutateurs \/dir \/o \/c doivent être spécifiés immédiatement après `Tools.Shell`.  Toute syntaxe spécifiée après le nom de l'exécutable est transmise en tant qu'argument de la ligne de commande.  
  
 L'alias prédéfini `Shell` peut être utilisé à la place de `Tools.Shell`.  
  
> [!CAUTION]
>  Si l'argument `path` fournit le chemin du répertoire et le nom du fichier, vous devez placer le nom de chemin d'accès tout entier entre guillemets \("""\), comme le montre l'exemple suivant :  
  
```  
Tools.Shell """C:\Program Files\SomeFile.exe"""  
```  
  
 Chacun groupe de trois guillemets \("""\) est interprété par le processeur `Shell` comme un seul caractère de guillemet.  Ainsi, l'exemple précédent passe en fait la chaîne de chemin suivante à la commande `Shell` :  
  
```  
"C:\Program Files\SomeFile.exe"  
```  
  
> [!CAUTION]
>  Si vous ne mettez pas la chaîne de chemin d'accès entre guillemets \("""\), Windows utilisera uniquement la partie de la chaîne jusqu'au premier espace.  Par exemple, si la chaîne de chemin d'accès ci\-dessus n'a pas été correctement mise entre guillemets, Windows rechercherait un fichier nommé « Program » situé dans le répertoire racine C:\\.  Si un fichier exécutable C:\\Program.exe était effectivement disponible, même installé de manière illicite, Windows essaierait d'exécuter ce programme à la place du programme « C:\\Program Files\\SomeFile.exe » voulu.  
  
## Exemple  
 La commande suivante utilise xcopy.exe pour copier le fichier `MyText.txt` dans le dossier `Text`.  La sortie de xcopy.exe s'affiche à la fois dans la fenêtre **Commande** et dans la fenêtre **Sortie**.  
  
```  
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Fenêtre Sortie](../../ide/reference/output-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)