---
title: Fonction SccQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3eefee11ed4db6e359688f2220c330bdbe81be1f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966036"
---
# <a name="sccqueryinfo-function"></a>Fonction SccQueryInfo
Cette fonction obtient les informations d’état pour un ensemble de fichiers sélectionnés sous contrôle de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte de plug-in de contrôle de source.  
  
 nFiles  
 [in] Nombre de fichiers spécifiés dans le `lpFileNames` tableau et la longueur de la `lpStatus` tableau.  
  
 lpFileNames  
 [in] Un tableau de noms de fichiers à interroger.  
  
 lpStatus  
 [in, out] Tableau dans lequel le plug-in de contrôle de code source retourne les indicateurs d’état pour chaque fichier. Pour plus d’informations, consultez [Code d’état de fichier](../extensibility/file-status-code-enumerator.md).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Requête a réussi.|  
|SCC_E_ACCESSFAILURE|Un problème avec l’accès au système de contrôle source, probablement dû à des problèmes de réseau ou de conflit est survenu. Une nouvelle tentative est recommandée.|  
|SCC_E_PROJNOTOPEN|Le projet n’est pas ouvert sous contrôle de code source.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Si `lpFileName` est une chaîne vide, il n’existe actuellement aucune information d’état pour mettre à jour. Sinon, il est le nom de chemin d’accès complet du fichier pour lequel les informations d’état peuvent ont été modifiés.  
  
 Le tableau de retour peut être un masque de bits de `SCC_STATUS_xxxx` bits. Pour plus d’informations, consultez [Code d’état de fichier](../extensibility/file-status-code-enumerator.md). Un système de contrôle de code source ne peut pas en charge tous les types de bit. Par exemple, si `SCC_STATUS_OUTOFDATE` n’est pas disponible, le bit n’est pas défini.  
  
 Lorsque vous utilisez cette fonction pour extraire des fichiers, notez les points suivants `MSSCCI` exigences d’état :  
  
-   `SCC_STATUS_OUTBYUSER` est définie lorsque l’utilisateur actuel a extrait le fichier.  
  
-   `SCC_STATUS_CHECKEDOUT` ne peut pas être définie, sauf si `SCC_STATUS_OUTBYUSER` est défini.  
  
-   `SCC_STATUS_CHECKEDOUT` est définie uniquement lorsque le fichier est extrait dans le répertoire de travail désigné.  
  
-   Si le fichier est extrait par l’utilisateur actuel dans un répertoire autre que le répertoire de travail `SCC_STATUS_OUTBYUSER` est défini mais `SCC_STATUS_CHECKEDOUT` n’est pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Code d’état de fichier](../extensibility/file-status-code-enumerator.md)