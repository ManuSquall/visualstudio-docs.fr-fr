---
title: Fonction de SccQueryInfo | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a178aada6303ed21f51a6be66ba02b2145dcd694
ms.lasthandoff: 02/22/2017

---
# <a name="sccqueryinfo-function"></a>SccQueryInfo (fonction)
Cette fonction obtient les informations d’état pour un ensemble de fichiers sélectionnés sous contrôle de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte du plug-in de contrôle de source.  
  
 nFiles  
 [in] Nombre de fichiers spécifié dans le `lpFileNames` tableau et la longueur de la `lpStatus` tableau.  
  
 lpFileNames  
 [in] Un tableau de noms de fichiers à interroger.  
  
 lpStatus  
 [dans, out] Tableau dans lequel le plug-in de contrôle de code source retourne les indicateurs d’état pour chaque fichier. Pour plus d’informations, consultez [fichier de Code d’état](../extensibility/file-status-code-enumerator.md).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|La requête a réussi.|  
|SCC_E_ACCESSFAILURE|Il a un problème avec l’accès au système de contrôle source, probablement dû à des problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_PROJNOTOPEN|Le projet n’est pas ouvert sous contrôle de code source.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Remarques  
 Si `lpFileName` est une chaîne vide, il n’existe actuellement aucune information d’état pour mettre à jour. Dans le cas contraire, il est le nom de chemin d’accès complet du fichier pour lequel les informations d’état peuvent ont changé.  
  
 Le tableau de retour peut être un masque de bits de `SCC_STATUS_xxxx` bits. Pour plus d’informations, consultez [fichier de Code d’état](../extensibility/file-status-code-enumerator.md). Un système de contrôle de source ne peut pas en charge tous les types de bits. Par exemple, si `SCC_STATUS_OUTOFDATE` n’est pas disponible, le bit n’est pas défini.  
  
 Lorsque vous utilisez cette fonction pour extraire des fichiers, notez les points suivants `MSSCCI` configuration requise d’état :  
  
-   `SCC_STATUS_OUTBYUSER`est définie lorsque l’utilisateur actuel a extrait le fichier.  
  
-   `SCC_STATUS_CHECKEDOUT`Impossible de définir `SCC_STATUS_OUTBYUSER` est défini.  
  
-   `SCC_STATUS_CHECKEDOUT`est définie uniquement lorsque le fichier est extrait dans le répertoire de travail spécifié.  
  
-   Si le fichier est extrait par l’utilisateur actuel dans un répertoire autre que le répertoire de travail `SCC_STATUS_OUTBYUSER` est défini mais `SCC_STATUS_CHECKEDOUT` n’est pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Code d’état de fichier](../extensibility/file-status-code-enumerator.md)
