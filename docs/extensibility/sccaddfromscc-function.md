---
title: Fonction de SccAddFromScc | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce2d9d179fd46bcc63340c911437486e1a459195
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139950"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc (fonction)
Cette fonction permet à l’utilisateur rechercher des fichiers qui se trouvent déjà dans le système de contrôle de code source puis en faire partie de ces fichiers du projet actuel. Par exemple, cette fonction peut obtenir un fichier d’en-tête commun dans le projet actuel sans copier le fichier. Le tableau de retour de fichiers, `lplpFileNames`, contient la liste des fichiers que l’utilisateur souhaite ajouter au projet IDE.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte plug-in de contrôle de code source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 lpnFiles  
 [dans, out] Pour le nombre de fichiers qui sont ajoutées à la mémoire tampon. (Il s’agit de `NULL` si la mémoire vers laquelle pointe `lplpFileNames` doit être libéré. Consultez la section Notes pour plus d’informations).  
  
 lplpFileNames  
 [dans, out] Tableau de pointeurs vers tous les noms de fichiers sans les chemins d’accès. Ce tableau est alloué et libéré par le plug-in de contrôle de code source. Si `lpnFiles` = 1 et `lplpFileNames` n’est pas `NULL`, le premier nom dans le tableau vers lequel pointe `lplpFileNames` contient le dossier de destination.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Les fichiers ont été correctement situés et ajoutés au projet.|  
|SCC_I_OPERATIONCANCELED|Opération annulée avec aucun effet.|  
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
  
## <a name="remarks"></a>Notes  
 L’IDE appelle cette fonction. Si le plug-in de contrôle de code source prend en charge la spécification d’un dossier local de destination, l’IDE passe `lpnFiles` = 1 et transmet le nom de dossier local dans `lplpFileNames`.  
  
 Lors de l’appel à la `SccAddFromScc` fonction retourne, le plug-in a attribué des valeurs à `lpnFiles` et `lplpFileNames`, allocation de la mémoire pour le tableau de nom de fichier si nécessaire (Notez que cette affectation remplace le pointeur dans `lplpFileNames`). Le plug-in de contrôle de code source est chargé de placer tous les fichiers dans le répertoire de l’utilisateur ou dans le dossier spécifié désignation. L’IDE ajoute ensuite les fichiers au projet IDE.  
  
 Enfin, l’IDE appelle cette fonction une seconde fois, en passant `NULL` pour `lpnFiles`. Ceci est interprété comme un signal spécial par le plug-in pour libérer la mémoire allouée pour le tableau de noms de fichiers dans le contrôle de code source `lplpFileNames``.`  
  
 `lplpFileNames` est un `char ***` pointeur. Le plug-in de contrôle de code source place un pointeur vers un tableau de pointeurs vers les noms de fichiers, par conséquent, en passant la liste de la manière standard pour cette API.  
  
> [!NOTE]
>  Les versions initiales de l’API VSSCI n’a pas fourni un moyen d’indiquer le projet cible pour les fichiers ajoutés. Pour tenir compte de cela, la sémantique de le `lplpFIleNames` paramètre ont été améliorées pour le rendre un paramètre d’entrée/sortie, plutôt qu’un paramètre de sortie. Si seul un fichier unique est spécifié, autrement dit, la valeur pointée par `lpnFiles` = 1, le premier élément du `lplpFileNames` contient le dossier cible. Pour utiliser cette nouvelle sémantique, les appels de l’IDE le `SccSetOption` fonctionne avec le `nOption`paramètre la valeur `SCC_OPT_SHARESUBPROJ`. Si un plug-in de contrôle de code source ne gère pas la sémantique, il renvoie `SCC_E_OPTNOTSUPPORTED`. Faire ce désactive l’utilisation de la **à partir du contrôle de code Source** fonctionnalité. Si le plug-in prend en charge la **à partir du contrôle de code Source** fonctionnalité (`SCC_CAP_ADDFROMSCC`), puis il doit prendre en charge la sémantique de nouveau et retourner `SCC_I_SHARESUBPROJOK`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)