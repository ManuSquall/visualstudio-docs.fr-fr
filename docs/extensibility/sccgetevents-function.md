---
title: Fonction de SccGetEvents | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetEvents
helpviewer_keywords: SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e2e9a22d0340774087fab8dd7dc564f415d9d9aa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetevents-function"></a>SccGetEvents (fonction)
Cette fonction récupère un événement d’état en file d’attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte plug-in de contrôle de code source.  
  
 lpFileName  
 [dans, out] Mémoire tampon dans lequel le plug-in de contrôle de code source place le nom de fichier retourné (_MAX_PATH caractères maximum).  
  
 lpStatus  
 [dans, out] Retourne le code d’état (consultez [Code d’état de fichier](../extensibility/file-status-code-enumerator.md) pour les valeurs possibles).  
  
 pnEventsRemaining  
 [dans, out] Retourne le nombre d’entrées restés dans la file d’attente après cet appel. Si ce nombre est élevé, l’appelant peut décider d’appeler le [SccQueryInfo](../extensibility/sccqueryinfo-function.md) pour obtenir toutes les informations à la fois.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Obtenir des événements a réussi.|  
|SCC_E_OPNOTSUPPORTED|Cette fonction n’est pas pris en charge.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction est appelée pendant le traitement inactif pour voir si des mises à jour d’état pour les fichiers sous contrôle de code source ont été. Le plug-in de contrôle de code source gère l’état de tous les fichiers qu’il connaît, et chaque fois qu’une modification de l’état est indiqué par le plug-in, l’état et le fichier associé sont stockés dans une file d’attente. Lorsque `SccGetEvents` est appelée, le haut l’élément de la file d’attente est récupéré et retourné. Cette fonction est limitée à retourner des informations précédemment mises en cache uniquement et doit avoir une très rapides (autrement dit, aucune lors de la lecture du disque ou demander du système de contrôle de source de l’état) ; dans le cas contraire, les performances de l’IDE peuvent démarrer à se dégrader.  
  
 S’il n’existe aucune mise à jour d’état au rapport, le plug-in de contrôle de code source stocke une chaîne vide dans la mémoire tampon pointée par `lpFileName`. Dans le cas contraire, le plug-in stocke le nom de chemin d’accès complet du fichier pour lequel les informations d’état a changé et retourne le code d’état appropriée (l’une des valeurs détaillées dans [Code d’état de fichier](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Code d’état de fichier](../extensibility/file-status-code-enumerator.md)