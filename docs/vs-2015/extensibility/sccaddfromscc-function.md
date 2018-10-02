---
title: Fonction SccAddFromScc | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d1dd8ee409fd1facae82a8b8c6eeb418a68b4a6b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494935"
---
# <a name="sccaddfromscc-function"></a>Fonction SccAddFromScc
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [fonction SccAddFromScc](https://docs.microsoft.com/visualstudio/extensibility/sccaddfromscc-function).  
  
Cette fonction permet à l’utilisateur rechercher des fichiers qui se trouvent déjà dans le système de contrôle source et apportez par la suite de ces fichiers faisant partie du projet actuel. Par exemple, cette fonction peut obtenir un fichier d’en-tête commun dans le projet actuel sans copier le fichier. Le tableau de résultats de fichiers, `lplpFileNames`, contient la liste des fichiers que l’utilisateur souhaite ajouter au projet IDE.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte de plug-in de contrôle de source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.  
  
 lpnFiles  
 [in, out] Une mémoire tampon pour le nombre de fichiers qui sont ajoutés dans. (Il s’agit de `NULL` si la mémoire vers laquelle pointe `lplpFileNames` doit être libéré. Consultez la section Notes pour plus d’informations).  
  
 lplpFileNames  
 [in, out] Un tableau de pointeurs vers tous les noms de fichier sans chemin de répertoire. Ce tableau est alloué et libéré par le plug-in de contrôle de code source. Si `lpnFiles` = 1 et `lplpFileNames` n’est pas `NULL`, le premier nom dans le tableau vers lequel pointe `lplpFileNames` contient le dossier de destination.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Les fichiers ont été correctement situés et ajoutés au projet.|  
|SCC_I_OPERATIONCANCELED|Opération a été annulée avec aucun effet.|  
|SCC_I_RELOADFILE|Un fichier ou un projet doit être rechargé.|  
  
## <a name="remarks"></a>Notes  
 L’IDE appelle cette fonction. Si le plug-in de contrôle de code source prend en charge la spécification d’un dossier local de destination, l’IDE passe `lpnFiles` = 1 et transmet le nom de dossier local dans `lplpFileNames`.  
  
 Lors de l’appel à la `SccAddFromScc` fonction retourne, le plug-in a attribué des valeurs à `lpnFiles` et `lplpFileNames`, allocation de mémoire pour le tableau de nom de fichier si nécessaire (Notez que cette allocation remplace le pointeur dans `lplpFileNames`). Le plug-in de contrôle de code source est chargé de placer tous les fichiers dans le répertoire de l’utilisateur ou dans le dossier de désignation spécifié. L’IDE ajoute ensuite les fichiers au projet IDE.  
  
 Enfin, l’IDE appelle cette fonction, une deuxième fois, en passant `NULL` pour `lpnFiles`. Ceci est interprété comme un signal spécial par le plug-in pour libérer la mémoire allouée pour le tableau de nom de fichier dans le contrôle de code source `lplpFileNames``.`  
  
 `lplpFileNames` est un `char ***` pointeur. Le plug-in de contrôle de code source place un pointeur vers un tableau de pointeurs vers des noms de fichiers, par conséquent, en passant la liste de la manière standard pour cette API.  
  
> [!NOTE]
>  Les versions initiales de l’API VSSCI n’a pas fourni un moyen d’indiquer le projet cible pour les fichiers ajoutés. Pour en tenir compte, la sémantique de le `lplpFIleNames` paramètre ont été améliorées pour le rendre un paramètre d’entrée/sortie plutôt que d’un paramètre de sortie. Si seul un seul fichier est spécifié, autrement dit, la valeur vers laquelle pointe `lpnFiles` = 1, le premier élément du `lplpFileNames` contient le dossier cible. Pour utiliser cette nouvelle sémantique, les appels de l’IDE le `SccSetOption` fonctionne avec le `nOption`paramètre défini sur `SCC_OPT_SHARESUBPROJ`. Si un plug-in de contrôle de code source ne prend pas en charge la sémantique, elle retourne `SCC_E_OPTNOTSUPPORTED`. Faire c’est le cas désactive l’utilisation de la **à partir du contrôle de code Source** fonctionnalité. Si un plug-in prend en charge la **à partir du contrôle de code Source** fonctionnalité (`SCC_CAP_ADDFROMSCC`), puis il doit prendre en charge la sémantique de nouveau et retourner `SCC_I_SHARESUBPROJOK`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)

