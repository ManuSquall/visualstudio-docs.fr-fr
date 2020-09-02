---
title: SccQueryInfo fonction) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f951e7ef29fbba7225997276b31bd9f32731efc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199982"
---
# <a name="sccqueryinfo-function"></a>Fonction SccQueryInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction obtient les informations d’état d’un ensemble de fichiers sélectionnés sous contrôle de code source.  
  
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
 dans Structure de contexte du plug-in de contrôle de code source.  
  
 Nfichiers  
 dans Nombre de fichiers spécifiés dans le `lpFileNames` tableau et longueur du `lpStatus` tableau.  
  
 lpFileNames  
 dans Tableau de noms des fichiers à interroger.  
  
 lpStatus  
 [in, out] Tableau dans lequel le plug-in de contrôle de code source retourne les indicateurs d’état de chaque fichier. Pour plus d’informations, consultez [code d’État du fichier](../extensibility/file-status-code-enumerator.md).  
  
## <a name="return-value"></a>Valeur renvoyée  
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|La requête a réussi.|  
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_PROJNOTOPEN|Le projet n’est pas ouvert sous le contrôle de code source.|  
|SCC_E_NONSPECIFICERROR|Échec non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Si `lpFileName` est une chaîne vide, il n’existe actuellement aucune information d’État à mettre à jour. Dans le cas contraire, il s’agit du nom de chemin d’accès complet du fichier pour lequel les informations d’État ont peut-être changé.  
  
 Le tableau de retour peut être un masque de `SCC_STATUS_xxxx` bits de bits. Pour plus d’informations, consultez [code d’État du fichier](../extensibility/file-status-code-enumerator.md). Un système de contrôle de code source ne prend peut-être pas en charge tous les types de bits. Par exemple, si `SCC_STATUS_OUTOFDATE` n’est pas proposé, le bit n’est pas défini.  
  
 Lorsque vous utilisez cette fonction pour extraire des fichiers, notez les `MSSCCI` conditions d’État suivantes :  
  
- `SCC_STATUS_OUTBYUSER` est défini lorsque l’utilisateur actuel a extrait le fichier.  
  
- `SCC_STATUS_CHECKEDOUT` ne peut pas être défini, sauf si `SCC_STATUS_OUTBYUSER` est défini.  
  
- `SCC_STATUS_CHECKEDOUT` la valeur est définie uniquement lorsque le fichier est extrait dans le répertoire de travail désigné.  
  
- Si le fichier est extrait par l’utilisateur actuel dans un répertoire autre que le répertoire de travail, `SCC_STATUS_OUTBYUSER` est défini mais `SCC_STATUS_CHECKEDOUT` pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)   
 [Code d’état de fichier](../extensibility/file-status-code-enumerator.md)
