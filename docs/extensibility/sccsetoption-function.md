---
title: Fonction de SccSetOption | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 916378ea594d14c9493535b3a28e72ea49ed4733
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143983"
---
# <a name="sccsetoption-function"></a>SccSetOption (fonction)
Cette fonction définit les options qui contrôlent le comportement du contrôle de source de plug-in.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte plug-in de contrôle de code source.  
  
 nOption  
 [in] L’option est définie.  
  
 dwVal  
 [in] Paramètres de l’option.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|L’option a été correctement définie.|  
|SCC_I_SHARESUBPROJOK|Retourné si `nOption` a été `SCC_OPT_SHARESUBPROJ` et le plug-in de contrôle de code source permet à l’IDE définir le dossier de destination.|  
|SCC_E_OPNOTSUPPORTED|L’option n’est pas définie et ne doit pas se reposer.|  
  
## <a name="remarks"></a>Notes  
 L’IDE appelle cette fonction pour contrôler le comportement du contrôle de source de plug-in. Le premier paramètre, `nOption`, indique la valeur est définie, tandis que le second, `dwVal`, indique que faire avec cette valeur. Le plug-in stocke ces informations associées à un `pvContext``,` l’IDE doit donc appeler cette fonction après avoir appelé la [SccInitialize](../extensibility/sccinitialize-function.md) (mais pas nécessairement après chaque appel à la [SccOpenProject](../extensibility/sccopenproject-function.md)).  
  
 Résumé des options et leurs valeurs :  
  
|`nOption`|`dwValue`|Description|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Active/désactive les événements queuing d’arrière-plan.|  
|`SCC_OPT_USERDATA`|Valeur arbitraire|Spécifie une valeur de l’utilisateur à passer à la [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) fonction de rappel.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indique si l’IDE prend actuellement en charge l’annulation d’une opération.|  
|`SCC_OPT_NAMECHANGEPFN`|Pointeur vers le [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) fonction de rappel|Définit un pointeur vers une fonction de rappel de changement de nom.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indique si l’IDE autorise la vérification de ses fichiers manuellement (via l’interface utilisateur du contrôle source) ou si elles doivent être extraits uniquement via le plug-in de contrôle de code source.|  
|`SCC_OPT_SHARESUBPROJ`|N/A|Si le plug-in de contrôle de code source permet à l’IDE spécifier le dossier de projet local, le plug-in retourne `SCC_I_SHARESUBPROJOK`.|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 Si `nOption` est `SCC_OPT_EVENTQUEUE`, l’IDE est la désactivation (ou réactiver) le traitement en arrière-plan. Par exemple, au cours d’une compilation, l’IDE peut demander le plug-in pour arrêter l’inactivité sur le traitement de tout type de contrôle de code source. Après la compilation, il serait réactiver traitement en arrière-plan à jour file d’attente du plug-in. Correspondant à la `SCC_OPT_EVENTQUEUE` valeur `nOption`, il existe deux valeurs possibles pour `dwVal`, à savoir, `SCC_OPT_EQ_ENABLE` et `SCC_OPT_EQ_DISABLE`.  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 Si la valeur de `nOption` est `SCC_OPT_HASCANCELMODE`, l’IDE permet aux utilisateurs d’annuler des opérations longues. Paramètre `dwVal` à `SCC_OPT_HCM_NO` (la valeur par défaut) indique que l’IDE n’a aucun mode d’annulation. Le plug-in de contrôle de code source doit proposer son propre bouton Annuler si elle souhaite que l’utilisateur pour pouvoir annuler. `SCC_OPT_HCM_YES` Indique que l’IDE fournit la possibilité d’annuler une opération, afin de l’analyse de plug-in n’a pas besoin d’afficher son propre bouton Annuler. Si l’IDE définit `dwVal` à `SCC_OPT_HCM_YES`, elle est prête à répondre aux `SCC_MSG_STATUS` et `DOCANCEL` les messages envoyés à la `lpTextOutProc` fonction de rappel (voir [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Si l’IDE ne définit pas cette variable, le plug-in ne doit pas envoyer ces deux messages.  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 Si nOption est définie sur `SCC_OPT_NAMECHANGEPFN`et à la fois la source de l’IDE et le plug-in de contrôle le permettent, le plug-in peut en fait de renommer ou déplacer un fichier pendant une opération de contrôle de code source. Le `dwVal` un pointeur de fonction de type a la valeur [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Pendant une opération de contrôle de code source, le plug-in peut appeler cette fonction, en passant dans trois paramètres. Il s’agit de l’ancien nom (avec le chemin d’accès qualifié complet) d’un fichier, le nouveau nom (avec le chemin d’accès qualifié complet) de ce fichier et un pointeur vers les informations qui s’applique à l’IDE. L’IDE envoie dans ce dernier pointeur en appelant `SccSetOption` avec `nOption` la valeur `SCC_OPT_USERDATA`, avec `dwVal` pointant vers les données. Prise en charge pour cette fonction est facultative. Un plug VSSCI-qu’utilise cette possibilité doit initialiser ses variables (fonction) les données utilisateur et de pointeur à `NULL`, et il ne doit pas appeler une fonction de changement de nom, sauf si elle a reçu un. Il doit également être préparé pour contenir la valeur qui lui a été attribué ou pour le modifier en réponse à un nouvel appel à `SccSetOption`. Cela ne se produit pas au milieu d’une opération de commande de contrôle de code source, mais il peut se produire entre les commandes.  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 Si nOption est définie sur `SCC_OPT_SCCCHECKOUTONLY`, l’IDE est indiquant que les fichiers dans le projet actuellement ouvert doivent jamais être récupérés manuellement via l’interface d’utilisateur du système de contrôle source. Au lieu de cela, les fichiers doivent être extrait uniquement via le contrôle de source de plug-in sous contrôle de l’IDE. Si `dwValue` a la valeur `SCC_OPT_SCO_NO`, cela signifie que les fichiers doivent être traitées normalement par le plug-in et peuvent être récupérés via l’interface utilisateur du contrôle de code source. Si `dwValue` est défini sur `SCC_OPT_SCO_YES`, puis seulement le plug-in est autorisé à extraire des fichiers et l’interface utilisateur du système de contrôle de source ne doit pas être appelée. Cela s’applique aux situations où l’IDE peut avoir « fichiers pseudo-aléatoire » qui se justifient pour extraire uniquement par le biais de l’IDE.  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 Si`nOption` a la valeur `SCC_OPT_SHARESUBPROJ`, l’IDE teste si le plug-in de contrôle de code source peut utiliser un dossier local spécifié lors de l’ajout de fichiers à partir du contrôle de code source. La valeur de le `dwVal` paramètre n’a pas d’importance dans ce cas. Si le plug-in permet à l’IDE spécifier le dossier local de destination où les fichiers sont ajoutés à partir de la source de contrôle lorsque le [SccAddFromScc](../extensibility/sccaddfromscc-function.md) est appelée, le plug-in doit retourner `SCC_I_SHARESUBPROJOK` lorsque le `SccSetOption` fonction est appelé. L’IDE utilise ensuite le `lplpFileNames` paramètre de la `SccAddFromScc` fonction à passer dans le dossier de destination. Le plug-in utilise ce dossier de destination pour placer les fichiers ajoutés à partir du contrôle de code source. Si le plug-in ne retourne pas `SCC_I_SHARESUBPROJOK` lors de la `SCC_OPT_SHARESUBPROJ` option est définie, l’IDE suppose que le plug-in est en mesure d’ajouter des fichiers uniquement dans le dossier local en cours.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)