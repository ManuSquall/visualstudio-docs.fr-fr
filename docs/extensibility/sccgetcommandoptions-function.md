---
title: Fonction de SccGetCommandOptions | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
caps.latest.revision: 14
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: df497de98463d728b5cd040415924a40fb6717b8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions (fonction)
Cette fonction invite l’utilisateur pour les options avancées pour une commande donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte plug-in de contrôle de code source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour toutes les boîtes de dialogue qu’il fournit.  
  
 iCommand  
 [in] La commande pour laquelle des options avancées sont demandées (consultez [le Code de commande](../extensibility/command-code-enumerator.md) pour les valeurs possibles).  
  
 ppvOptions  
 [in] La structure de l’option (peut également être `NULL`).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Opération réussie.|  
|SCC_I_ADV_SUPPORT|Le plug-in de contrôle de code source prend en charge les options avancées pour la commande.|  
|SCC_I_OPERATIONCANCELED|L’utilisateur a annulé la source contrôle du plug-in **Options** boîte de dialogue.|  
|SCC_E_OPTNOTSUPPORTED|Le plug-in de contrôle de code source ne prend pas en charge cette opération.|  
|SCC_E_ISCHECKEDOUT|Impossible d’effectuer cette opération sur un fichier qui est actuellement extrait.|  
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention. Une nouvelle tentative est recommandée.|  
|SCC_E_NONSPECIFICERROR|Erreur non spécifique.|  
  
## <a name="remarks"></a>Remarques  
 L’IDE appelle cette fonction pour la première fois avec `ppvOptions` = `NULL` pour déterminer si le plug-in de contrôle de code source prend en charge la fonctionnalité des options avancées pour la commande spécifiée. Si le plug-in prend en charge la fonctionnalité de cette commande, l’IDE appelle cette fonction à nouveau lorsque l’utilisateur demande des options avancées (généralement implémenté comme un **avancé** bouton dans une boîte de dialogue) et fournit un pointeur non NULL pour `ppvOptions` qui pointe vers un `NULL` pointeur. Stocke des options avancées, spécifiées par l’utilisateur dans une structure private et la retourne un pointeur vers cette structure dans le plug-in `ppvOptions`. Cette structure est ensuite transmise à toutes les autres fonctions d’API de plug-in de contrôle de code Source qui doivent en être informés, y compris les appels suivants à la `SccGetCommandOptions` (fonction).  
  
 Un exemple peut aider à clarifier cette situation.  
  
 Un utilisateur choisit le **obtenir** commande et l’IDE affiche un **obtenir** boîte de dialogue. Les appels de l’IDE le `SccGetCommandOptions` fonctionne avec `iCommand` la valeur `SCC_COMMAND_GET` et `ppvOptions` la valeur `NULL`. Ceci est interprété par le plug-in en tant que la question de contrôle de code source, « Avez-vous des options avancées pour cette commande ? » Si le plug-in de retourne `SCC_I_ADV_SUPPORT`, l’IDE affiche un **avancé** bouton dans son **obtenir** boîte de dialogue.  
  
 La première fois que l’utilisateur clique sur le **avancé** bouton, l’IDE appelle de nouveau la `SccGetCommandOptions` de fonction, cette fois avec un non -`NULL``ppvOptions` qui pointe vers un `NULL` pointeur. Le plug-in affiche sa propre **obtenir des Options de** boîte de dialogue invite l’utilisateur pour plus d’informations, placer cette information dans sa propre structure et retourne un pointeur vers cette structure dans `ppvOptions`.  
  
 Si l’utilisateur clique sur **avancé** dans la boîte de dialogue, l’IDE appelle de nouveau la `SccGetCommandOptions` fonction sans modification `ppvOptions`, de sorte que la structure est repassée au plug-in. Ainsi, le plug-in de réinitialisation de la boîte de dialogue pour les valeurs que l’utilisateur a défini précédemment. Le plug-in modifie la structure en place avant de retourner.  
  
 Enfin, lorsque l’utilisateur clique sur **OK** dans l’IDE **obtenir** boîte de dialogue, les appels de l’IDE le [SccGet](../extensibility/sccget-function.md), en passant la structure retournée dans `ppvOptions` qui contient le options avancées.  
  
> [!NOTE]
>  La commande `SCC_COMMAND_OPTIONS` est utilisé lors de l’IDE affiche un **Options** boîte de dialogue qui permet à l’utilisateur de définie les préférences qui contrôlent le fonctionne de l’intégration. Si le plug-in de contrôle de code source souhaite fournir sa propre boîte de dialogue Préférences, il peut afficher à partir une **avancé** bouton dans la boîte de dialogue Préférences de l’IDE. Le plug-in est uniquement responsable de l’obtention et la conservation de ces informations ; l’IDE ne pas utiliser ou modifier.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Code de commande](../extensibility/command-code-enumerator.md)
