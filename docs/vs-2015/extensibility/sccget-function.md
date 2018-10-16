---
title: Fonction SccGet | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb6f5204b1605969a37fd6528dda0ccaa7b8fe7f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175199"
---
# <a name="sccget-function"></a>Fonction SccGet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction récupère une copie d’un ou plusieurs fichiers pour l’affichage et la compilation, mais ne pas pour la modification. Dans la plupart des systèmes, les fichiers sont marqués comme étant en lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte du plug-in de contrôle de code source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.  
  
 nFiles  
 [in] Nombre de fichiers spécifiés dans le `lpFileNames` tableau.  
  
 lpFileNames  
 [in] Tableau des noms qualifiés complets de fichiers à récupérer.  
  
 Options  
 [in] Indicateurs de commande (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 pvOptions  
 [in] Options spécifiques au plug-in de contrôle source.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Succès de l’opération get.|  
|SCC_E_FILENOTCONTROLLED|Le fichier n’est pas sous contrôle de code source.|  
|SCC_E_OPNOTSUPPORTED|Le système de contrôle de code source ne prend pas en charge cette opération.|  
|SCC_E_FILEISCHECKEDOUT|Impossible d’obtenir le fichier que l’utilisateur a extrait.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_NOSPECIFIEDVERSION|Version non valide ou date/heure spécifié.|  
|SCC_E_NONSPECIFICERROR|Échec non spécifique ; fichier n’a pas été synchronisé.|  
|SCC_I_OPERATIONCANCELED|Opération annulée avant la fin.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer cette opération.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction est appelée avec un nombre et un tableau de noms des fichiers à récupérer. Si l’IDE passe l’indicateur `SCC_GET_ALL`, cela signifie que les éléments dans `lpFileNames` ne sont pas des fichiers, mais les répertoires et tous les fichiers sous contrôle de code source dans les répertoires donnés doivent être récupérés.  
  
 Le `SCC_GET_ALL` indicateur peut être combiné avec le `SCC_GET_RECURSIVE` indicateur pour récupérer tous les fichiers dans les répertoires donnés et tous les sous-répertoires.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` ne doit jamais être passé sans `SCC_GET_ALL`. En outre, notez que si les répertoires C:\A et C:\A\B sont tous deux passé sur une récursive obtenir, C:\A\B et tous ses sous-répertoires seront réellement récupérés à deux reprises. Il incombe de l’IDE, et pas la source de contrôle du plug-in, pour vous assurer que les doublons telle que celle-ci sont conservées hors du tableau.  
  
 Enfin, même si un contrôle de source plug-in spécifié le `SCC_CAP_GET_NOUI` indicateur lors de l’initialisation, indiquant alors qu’il n’a pas une interface utilisateur pour une commande Get, cette fonction peut toujours être appelée par l’IDE pour récupérer des fichiers. L’indicateur signifie simplement que l’IDE n’affiche pas d’un élément de menu Get et que le plug-in n’est pas supposé fournir toute interface utilisateur.  
  
## <a name="renaming-and-sccget"></a>Changement de nom et SccGet  
 Situation : un utilisateur extrait un fichier, par exemple, a.txt et le modifie. Avant que ne a.txt peut être archivé, un second utilisateur renomme le fichier a.txt en b.txt dans la base de données de contrôle de code source, extrait b.txt, met quelques modifications au fichier et vérifie le fichier. Le premier utilisateur veut les modifications apportées par le second utilisateur pour le premier utilisateur renomme leur version locale du fichier a.txt en b.txt et qu’il effectue une opération get sur le fichier. Toutefois, le cache local qui effectue le suivi des numéros de version croit toujours la première version d’un fichier a.txt est stockée localement et par conséquent, contrôle de code source ne peut pas résoudre les différences.  
  
 Il existe deux manières de résoudre cette situation où le cache local des versions de contrôle de code source est désynchronisé avec la base de données de contrôle de code source :  
  
1.  N’autorisez pas la modification du nom d’un fichier dans la base de données de contrôle de code source qui est actuellement extrait.  
  
2.  Effectuer l’équivalent de « suppression ancien » suivie de « Ajouter ». L’algorithme suivant est une façon d’y parvenir.  
  
    1.  Appelez le [SccQueryChanges](../extensibility/sccquerychanges-function.md) (fonction) pour en savoir plus sur le changement de nom d’un fichier a.txt en b.txt dans la base de données de contrôle de code source.  
  
    2.  Renommez le fichier a.txt local en b.txt.  
  
    3.  Appelez le `SccGet` (fonction) pour le fichier a.txt et b.txt.  
  
    4.  Étant donné que le fichier a.txt n’existe pas dans la base de données de contrôle de code source, le cache de la version locale est purgé des informations de version a.txt manquantes.  
  
    5.  Le fichier b.txt en cours d’extraction est fusionné avec le contenu du fichier b.txt local.  
  
    6.  Le fichier b.txt mis à jour peut désormais être archivé.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)

