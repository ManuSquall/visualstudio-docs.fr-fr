---
title: Fonction SccIsMultiCheckoutEnabled | Microsoft Docs
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
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 11bd525d90f6c593c7a78de5734fa2b2e718c9db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507877"
---
# <a name="sccismulticheckoutenabled-function"></a>Fonction SccIsMultiCheckoutEnabled
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [fonction SccIsMultiCheckoutEnabled](https://docs.microsoft.com/visualstudio/extensibility/sccismulticheckoutenabled-function).  
  
Cette fonction vérifie si le plug-in de contrôle de code source autorise les extractions multiples sur un fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 [in] La structure de contexte de plug-in de contrôle de source.  
  
 pbMultiCheckout  
 [out] Spécifie si les extractions multiples sont activées pour ce projet (différente de zéro signifie que les extractions multiples sont pris en charge).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|La vérification a réussi.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Notes  
 L’IDE effectue deux vérifications pour déterminer si les fichiers peuvent être extraits simultanément par plusieurs utilisateurs. Tout d’abord, le système de contrôle de source doit prendre en charge les extractions multiples. Le plug-in de contrôle de code source peut spécifier cette fonctionnalité lors de l’initialisation en spécifiant le `SCC_CAP_MULTICHECKOUT`. Par la suite, une deuxième vérification, l’IDE appelle cette fonction pour déterminer si le projet actuel prend en charge les extractions multiples. Si les extractions multiples sont pris en charge pour le projet sélectionné, la plug-in retourne une réussite de code et définit `pbMultiCheckout` à différente de zéro (`TRUE`) ou `FALSE`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)

