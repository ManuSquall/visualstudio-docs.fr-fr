---
title: "SccAddFromScc (fonction) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAddFromScc"
helpviewer_keywords: 
  - "SccAddFromScc (fonction)"
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccAddFromScc (fonction)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette fonction permet à l'utilisateur rechercher des fichiers qui se trouvent déjà dans le système de contrôle source et faire partie de ces fichiers du projet actuel. Par exemple, cette fonction peut obtenir un fichier d'en\-tête commun dans le projet actuel sans copier le fichier. Le tableau de fichiers, retour `lplpFileNames`, contient la liste des fichiers que l'utilisateur souhaite ajouter au projet IDE.  
  
## Syntaxe  
  
```cpp#  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### Paramètres  
 pvContext  
 \[in\] La structure de contexte du plug\-in de contrôle de source.  
  
 hWnd  
 \[in\] Handle vers la fenêtre de l'IDE que le plug\-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu'il fournit.  
  
 lpnFiles  
 \[dans, out\] Le nombre de fichiers qui sont ajoutées à la mémoire tampon. \(Il s'agit de `NULL` Si la mémoire pointée par `lplpFileNames` doit être libéré. Consultez la section Notes pour plus d'informations\).  
  
 lplpFileNames  
 \[dans, out\] Tableau de pointeurs vers tous les noms de fichier sans chemin de répertoire. Ce tableau est alloué et libéré par le plug\-in de contrôle de code source. Si `lpnFiles` \= 1 et `lplpFileNames` n'est pas `NULL`, le premier nom dans le tableau vers lequel pointe `lplpFileNames` contient le dossier de destination.  
  
## Valeur de retour  
 L'implémentation de plug\-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|------------|-----------------|  
|SCC\_OK|Les fichiers ont été correctement situés et ajoutés au projet.|  
|SCC\_I\_OPERATIONCANCELED|Opération annulée sans effet.|  
|SCC\_I\_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
  
## Notes  
 L'IDE appelle cette fonction. Si le plug\-in de contrôle de code source prend en charge la spécification d'un dossier local de destination, l'IDE passe `lpnFiles` \= 1 et transmet le nom de dossier local dans `lplpFileNames`.  
  
 Lors de l'appel à la `SccAddFromScc` fonction retourne, le plug\-in a attribué des valeurs à `lpnFiles` et `lplpFileNames`, allocation de la mémoire pour le tableau de noms de fichier si nécessaire \(Notez que cette affectation remplace le pointeur dans `lplpFileNames`\). Le plug\-in de contrôle de code source est chargé de placer tous les fichiers dans le répertoire de l'utilisateur ou dans le dossier de l'unité spécifiée. L'IDE ajoute ensuite les fichiers au projet IDE.  
  
 Enfin, l'IDE appelle cette fonction une seconde fois, en transmettant `NULL` pour `lpnFiles`. Ceci est interprété comme un signal spécial par plug\-in pour libérer la mémoire allouée au tableau de noms de fichiers dans le contrôle de code source `lplpFileNames``.`  
  
 `lplpFileNames` est un `char ***` pointeur. Le plug\-in de contrôle de code source place un pointeur vers un tableau de pointeurs vers les noms de fichiers, donc en passant la liste de la manière standard pour cette API.  
  
> [!NOTE]
>  Les versions initiales de l'API VSSCI n'a pas fourni un moyen d'indiquer le projet cible pour les fichiers ajoutés. Pour tenir compte de cela, la sémantique de le `lplpFIleNames` paramètre ont été améliorées pour rendre un paramètre d'entrée\/sortie plutôt que d'un paramètre de sortie. Si seul un fichier unique est spécifié, autrement dit, la valeur pointée par `lpnFiles` \= 1, le premier élément de `lplpFileNames` contient le dossier cible. Pour utiliser cette nouvelle sémantique, les appels IDE le `SccSetOption` fonctionne avec le `nOption`paramètre la valeur `SCC_OPT_SHARESUBPROJ`. Si un plug\-in de contrôle de code source ne prend pas en charge la sémantique, il renvoie `SCC_E_OPTNOTSUPPORTED`. Cela désactive ce l'utilisation de la **à partir du contrôle de code Source** fonctionnalité. Si un plug\-in prend en charge le **à partir du contrôle de code Source** fonctionnalité \(`SCC_CAP_ADDFROMSCC`\), puis il doit prendre en charge la nouvelle sémantique et retourner `SCC_I_SHARESUBPROJOK`.  
  
## Voir aussi  
 [Fonctions d'API de plug\-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)