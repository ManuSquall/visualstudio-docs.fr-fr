---
title: 'IDispatchEx :: InvokeEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a15acb3211c0d3dd19c0d262efb6cbd3327ab9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575316"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Fournit l’accès aux propriétés et aux méthodes exposées par un objet `IDispatchEx`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `id`  
 Identifie le membre. Utilise `GetDispID` ou `GetNextDispID` pour obtenir l’identificateur de dispatch.  
  
 `lcid`  
 Contexte des paramètres régionaux dans lequel interpréter les arguments. Le `lcid` est passé à `InvokeEx` pour permettre à l’objet d’interpréter ses arguments spécifiques à des paramètres régionaux.  
  
 `wFlags`  
 Les valeurs autorisées pour `wFlags` sont les suivantes :  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Indicateurs décrivant le contexte de l’appel de `InvokeEx` :  
  
|valeur|Signification|  
|-----------|-------------|  
|DISPATCH_METHOD|Le membre est appelé en tant que méthode. Si une propriété porte le même nom, vous pouvez définir à la fois cet indicateur et l’indicateur DISPATCH_PROPERTYGET (défini par `IDispatch`).|  
|DISPATCH_PROPERTYGET|Le membre est récupéré en tant que propriété ou membre de données (défini par `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Le membre est modifié en tant que propriété ou membre de données (défini par `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Le membre est modifié par une assignation de référence plutôt qu’une assignation de valeur. Cet indicateur est valide uniquement lorsque la propriété accepte une référence à un objet (défini par `IDispatch`).|  
|DISPATCH_CONSTRUCT|Le membre est utilisé en tant que constructeur. (Il s’agit d’une nouvelle valeur définie par `IDispatchEx`). Les valeurs autorisées pour `wFlags` sont les suivantes :<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Pointeur vers une structure qui contient un tableau d'arguments, un tableau d'arguments DISPID pour les arguments nommés et le nombre d'éléments de chaque tableau. Consultez la documentation `IDispatch` pour obtenir une description complète de la structure DISPPARAMS.  
  
 `pVarRes`  
 Pointeur vers l’emplacement où le résultat doit être stocké ou null si l’appelant n’attend aucun résultat. Cet argument est ignoré si DISPATCH_PROPERTYPUT ou DISPATCH_PROPERTYPUTREF est spécifié.  
  
 `pei`  
 Pointeur vers une structure qui contient les informations sur les exceptions. Cette structure doit être remplie si `DISP_E_EXCEPTION` est retourné. Peut avoir la valeur null. Consultez la documentation `IDispatch` pour obtenir une description complète de la structure de `EXCEPINFO`.  
  
 `pspCaller`  
 Pointeur vers un objet de fournisseur de services fourni par l’appelant, ce qui permet à l’objet d’obtenir des services de l’appelant. Peut avoir la valeur null.  
  
 `IDispatchEx::InvokeEx` fournit les mêmes fonctionnalités que `IDispatch::Invoke` et ajoute quelques extensions :  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Indique que l’élément est utilisé en tant que constructeur.|  
|`pspCaller`|Le `pspCaller` permet à l’objet d’accéder aux services fournis par l’appelant. Les services spécifiques peuvent être gérés par l’appelant lui-même ou être délégué aux appelants plus loin dans la chaîne d’appel. Par exemple, si un moteur de script à l’intérieur d’un navigateur effectue un appel de `InvokeEx` à un objet externe, l’objet peut suivre la chaîne `pspCaller` pour obtenir des services à partir du moteur de script ou du navigateur. (Notez que la chaîne d’appel n’est pas la même que la chaîne de création, également appelée chaîne de conteneur ou chaîne de site. La chaîne de création peut être disponible par le biais d’un autre mécanisme tel que `IObjectWithSite`.)|  
|Pointeur `this`|Quand DISPATCH_METHOD est défini dans `wFlags`, il peut y avoir un « paramètre nommé » pour la valeur « This ». Le DISPID sera DISPID_THIS et il doit être le premier paramètre nommé.|  
  
 Le paramètre de `riid` inutilisé dans `IDispatch::Invoke` a été supprimé.  
  
 Le paramètre `puArgArr` dans `IDispatch::Invoke` a été supprimé.  
  
 Consultez la documentation `IDispatch::Invoke` pour les exemples suivants :  
  
 « Appel d’une méthode sans argument »  
  
 « Obtention et définition des propriétés »  
  
 « Passage des paramètres »  
  
 « Propriétés indexées »  
  
 « Déclenchement d’exceptions lors de l’appel »  
  
 « Erreurs de retour »  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Opération réussie.|  
|DISP_E_BADPARAMCOUNT|Le nombre d’éléments fournis à DISPPARAMS est différent du nombre d’arguments acceptés par la méthode ou la propriété.|  
|DISP_E_BADVARTYPE|L’un des arguments de `rgvarg` n’est pas un type Variant valide.|  
|DISP_E_EXCEPTION|L’application doit lever une exception. Dans ce cas, la structure passée dans `pei` doit être remplie.|  
|DISP_E_MEMBERNOTFOUND|Le membre demandé n’existe pas, ou l’appel à `InvokeEx` a essayé de définir la valeur d’une propriété en lecture seule.|  
|DISP_E_NONAMEDARGS|Cette implémentation de `IDispatch` ne prend pas en charge les arguments nommés.|  
|DISP_E_OVERFLOW|L’un des arguments de `rgvarg` n’a pas pu être forcé au type spécifié.|  
|DISP_E_PARAMNOTFOUND|L’un des DISPID du paramètre ne correspond pas à un paramètre de la méthode.|  
|DISP_E_TYPEMISMATCH|Un ou plusieurs des arguments n’ont pas pu être forcés.|  
|DISP_E_UNKNOWNLCID|Le membre appelé interprète les arguments de chaîne en fonction du LCID et le LCID n’est pas reconnu. Si le LCID n’est pas nécessaire pour interpréter les arguments, cette erreur ne doit pas être retournée.|  
|DISP_E_PARAMNOTOPTIONAL|Un paramètre obligatoire a été omis.|  
  
## <a name="example"></a>Exemple  
  
```cpp
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)  
 [IDispatchEx :: GetDispID](../../winscript/reference/idispatchex-getdispid.md)    
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)