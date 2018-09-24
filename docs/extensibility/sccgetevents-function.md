---
title: Fonction SccGetEvents | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 21cc159f4ea09d817e81f74f338cc748833e1b62
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636939"
---
# <a name="sccgetevents-function"></a>Fonction SccGetEvents
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
  
### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte de plug-in de contrôle de source.  
  
 lpFileName  
 [in, out] Mémoire tampon où le plug-in de contrôle de code source place le nom de fichier renvoyé (_MAX_PATH caractères maximum).  
  
 lpStatus  
 [in, out] Retourne le code d’état (consultez [fichier de code d’état](../extensibility/file-status-code-enumerator.md) pour les valeurs possibles).  
  
 pnEventsRemaining  
 [in, out] Retourne le nombre d’entrées restés dans la file d’attente après cet appel. Si ce nombre est élevé, l’appelant peut décider d’appeler le [SccQueryInfo](../extensibility/sccqueryinfo-function.md) pour obtenir toutes les informations à la fois.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Obtenir les événements réussis.|  
|SCC_E_OPNOTSUPPORTED|Cette fonction n’est pas pris en charge.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 Cette fonction est appelée pendant le traitement inactif pour voir si des mises à jour d’état pour les fichiers sous contrôle de code source ont été. Le plug-in de contrôle de code source gère l’état de tous les fichiers qu’il connaît, et chaque fois qu’une modification de l’état est indiqué par le plug-in, l’état et le fichier associé sont stockés dans une file d’attente. Lorsque `SccGetEvents` est appelée, le haut l’élément de la file d’attente est récupéré et retourné. Cette fonction est limitée pour retourner uniquement des informations mises en cache précédemment et doit avoir un temps de réponse très rapide (autrement dit, aucune lecture du disque ou demandant le système de contrôle de code source pour l’état) ; dans le cas contraire, les performances de l’IDE peuvent démarrer à se dégrader.  
  
 S’il n’existe aucune mise à jour d’état au rapport, le plug-in de contrôle de code source stocke une chaîne vide dans la mémoire tampon vers laquelle pointée `lpFileName`. Sinon, le plug-in stocke le nom de chemin d’accès complet du fichier pour lequel les informations d’état a changé et retourne le code d’état approprié (l’une des valeurs détaillées dans [fichier de code d’état](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API source contrôle plug-in](../extensibility/source-control-plug-in-api-functions.md)   
 [Code d’état de fichier](../extensibility/file-status-code-enumerator.md)