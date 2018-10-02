---
title: FRAMEINFO_FLAGS | Microsoft Docs
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
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d1ec38f973b51124062fe77c6fab00e9d964cedc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493015"
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [FRAMEINFO_FLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/frameinfo-flags).  
  
Spécifie les informations permettant de récupérer sur un objet de frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```csharp  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>Membres  
 FIF_FUNCNAME  
 Initialize/utiliser le `m_bstrFuncName` champ.  
  
 FIF_RETURNTYPE  
 Initialize/utiliser le `m_bstrReturnType` champ.  
  
 FIF_ARGS  
 Initialize/utiliser le `m_bstrArgs` champ.  
  
 FIF_LANGUAGE  
 Initialize/utiliser le `m_bstrLanguage` champ.  
  
 FIF_MODULE  
 Initialize/utiliser le `m_bstrModule` champ.  
  
 FIF_STACKRANGE  
 Initialize/utiliser le `m_addrMin` et `m_addrMax` champs (plage de pile).  
  
 FIF_FRAME  
 Initialize/utiliser le `m_pFrame` champ.  
  
 FIF_DEBUGINFO  
 Initialize/utiliser le `m_fHasDebugInfo` champ.  
  
 FIF_STALECODE  
 Initialize/utiliser le `m_fStaleCode` champ.  
  
 FIF_ANNOTATEDFRAME  
 Initialize/utiliser le `m_fAnnotatedFrame` champ.  
  
 FIF_DEBUG_MODULEP  
 Initialize/utiliser le `m_pModule` champ.  
  
 FIF_FUNCNAME_FORMAT  
 Met en forme le nom de fonction. Le résultat est retourné dans le `m_bstrFunName` champ et aucun autres champs sont renseignés.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Ajoute le type de retour à la `m_bstrFuncName` champ.  
  
 FIF_FUNCNAME_ARGS  
 Ajoute les arguments à la `m_bstrFuncName` champ.  
  
 FIF_FUNCNAME_LANGUAGE  
 Ajoute la langue à la `m_bstrFuncName` champ.  
  
 FIF_FUNCNAME_MODULE  
 Ajoute le nom du module à le `m_bstrFuncName` champ.  
  
 FIF_FUNCNAME_LINES  
 Ajoute le nombre de lignes à la `m_bstrFuncName` champ.  
  
 FIF_FUNCNAME_OFFSET  
 Ajoute à la `m_bstrFuncName` champ offset en octets à partir du début de la ligne si `FIF_FUNCNAME_LINES` est spécifié. Si `FIF_FUNCNAME_LINES` n’est pas spécifié, ou si les numéros de ligne ne sont pas disponibles, ajoute le décalage en octets à partir du début de la fonction.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Ajoute le type de chaque argument de fonction pour le `m_bstrFuncName` champ.  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Ajoute le nom de chaque argument de fonction pour le `m_bstrFuncName` champ.  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Ajoute la valeur de chaque argument de fonction pour le `m_bstrFuncName` champ.  
  
 FIF_FUNCNAME_ARGS_ALL  
 Ajoute le type, le nom et la valeur de tous les arguments pour le `m_bstrFuncName` champ.  
  
 FIF_ARGS_TYPES  
 Les types d’arguments sont récupérés et mis en forme.  
  
 FIF_ARGS_NAMES  
 Les noms des arguments sont récupérés et mis en forme.  
  
 FIF_ARGS_VALUES  
 Les valeurs d’argument sont récupérés et mis en forme.  
  
 FIF_ARGS_ALL  
 Récupérer et mettre en forme le type, le nom et la valeur de tous les arguments.  
  
 FIF_ARGS_NOFORMAT  
 Spécifie que les arguments ne sont pas formatées (par exemple, ne pas ajouter des parenthèses autour de la liste d’arguments ni ajouter un séparateur entre arguments).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 Spécifie que l’évaluation de fonction (propriété) ne doit pas être utilisée lors de la récupération des valeurs d’argument.  
  
 FIF_FILTER_NON_USER_CODE  
 Le moteur de débogage consiste à filtrer les frames de code de non-utilisateur afin qu’ils ne soient pas inclus.  
  
 FIF_ARGS_NO_TOSTRING  
 Ne pas autoriser `ToString()` fonction d’évaluation ou de mise en forme lors du renvoi des arguments de fonction.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 Informations de frame doivent être obtenues à partir du domaine d’application hébergé plutôt que le processus d’hébergement.  
  
## <a name="remarks"></a>Notes  
 Ces indicateurs sont passées à la [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) et [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) méthodes pour indiquer quels champs doivent être initialisés dans le [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structure ou structures.  
  
 Ces indicateurs sont également utilisées pour indiquer les champs de la [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structure sont utilisées et valide lors de la structure est retournée. Ces valeurs peuvent être combinées avec un opérateur de bits `OR`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)

