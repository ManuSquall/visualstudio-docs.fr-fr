---
title: IDispatchEx::InvokeEx | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.InvokeEx
apilocation: scrobj.dll
helpviewer_keywords: InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6302228b110e2b0a6296190079bf60b3d92980bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Fournit l’accès aux propriétés et méthodes exposées par un `IDispatchEx` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Contexte des paramètres régionaux dans lequel interpréter les arguments. Le `lcid` est passé à `InvokeEx` pour permettre à l’objet interpréter les arguments spécifiques aux paramètres régionaux.  
  
 `wFlags`  
 Les valeurs autorisées pour `wFlags` sont :  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Indicateurs décrivant le contexte de la `InvokeEx` appeler :  
  
|Valeur|Signification|  
|-----------|-------------|  
|DISPATCH_METHOD|Le membre est appelé comme une méthode. Si une propriété a le même nom, cela et l’indicateur DISPATCH_PROPERTYGET peut être défini (défini par `IDispatch`).|  
|DISPATCH_PROPERTYGET|Le membre est récupéré sous la forme d’un propriété ou membre de données (définies par `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Le membre est modifié en tant que propriété ou donnée membre (définie par `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Le membre est modifié par une assignation de référence plutôt que par une attribution de valeur. Cet indicateur n’est valide uniquement lorsque la propriété accepte une référence à un objet (défini par `IDispatch`).|  
|DISPATCH_CONSTRUCT|Le membre est utilisé en tant que constructeur. (Il s’agit d’une nouvelle valeur définie par `IDispatchEx`). Les valeurs autorisées pour `wFlags` sont :<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Pointeur vers une structure qui contient un tableau d’arguments, un tableau d’arguments DISPID pour les arguments nommés et le nombre d’éléments de chaque tableau. Consultez le `IDispatch` documentation pour obtenir une description complète de la structure DISPPARAMS.  
  
 `pVarRes`  
 Pointeur vers l’emplacement où le résultat doit être stockée ou Null si l’appelant s’attend à aucun résultat. Cet argument est ignoré si DISPATCH_PROPERTYPUT ou DISPATCH_PROPERTYPUTREF est spécifié.  
  
 `pei`  
 Pointeur vers une structure qui contient les informations sur les exceptions. Cette structure doit être remplie lorsque `DISP_E_EXCEPTION` est retourné. Peut être Null. Consultez le `IDispatch` documentation pour obtenir une description complète de la `EXCEPINFO` structure.  
  
 `pspCaller`  
 Pointeur vers un objet de fournisseur de service fourni par l’appelant, qui permet à l’objet obtenir des services à partir de l’appelant. Peut être Null.  
  
 `IDispatchEx::InvokeEx`fournit les mêmes fonctionnalités que `IDispatch::Invoke` et ajoute quelques extensions :  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Indique que l’élément est utilisé en tant que constructeur.|  
|`pspCaller`|Le `pspCaller` permet à l’objet d’accéder aux services fournis par l’appelant. Services spécifiques peuvent être gérées par l’appelant lui-même ou déléguées aux appelants plus haut de la chaîne d’appel. Par exemple, si un moteur de script à l’intérieur d’un navigateur rend une `InvokeEx` appel à un objet externe, l’objet peut suivre le `pspCaller` chaîne pour obtenir des services à partir du moteur de script ou d’un navigateur. (Notez que la chaîne d’appel n’est pas identique à la chaîne de la création, également appelée la chaîne de conteneur ou la chaîne de site. La chaîne de création peut-être être disponible via d’autres mécanismes tels que `IObjectWithSite`.)|  
|Pointeur `this`|Lorsque DISPATCH_METHOD a la valeur `wFlags`, il peut y avoir un paramètre « nommé » pour la valeur de « THI ». Le DISPID sera DISPID_THIS, et il doit être le premier paramètre nommé.|  
  
 Non `riid` paramètre `IDispatch::Invoke` a été supprimé.  
  
 Le `puArgArr` paramètre `IDispatch::Invoke` a été supprimé.  
  
 Consultez le `IDispatch::Invoke` documentation pour les exemples suivants :  
  
 « Appel d’une méthode sans arguments »  
  
 « Obtention et définition des propriétés »  
  
 « Passage de paramètres »  
  
 « Propriétés indexées »  
  
 « Le déclenchement d’exceptions pendant Invoke »  
  
 « Retour d’erreur »  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Opération réussie.|  
|DISP_E_BADPARAMCOUNT|Le nombre d’éléments fournie pour DISPPARAMS est différent du nombre d’arguments acceptés par la méthode ou propriété.|  
|DISP_E_BADVARTYPE|Un des arguments de `rgvarg` n’est pas un type variant valide.|  
|DISP_E_EXCEPTION|L’application doit lever une exception. Dans ce cas, la structure passée dans `pei` doit être renseigné.|  
|DISP_E_MEMBERNOTFOUND|Le membre demandé n’existe pas, ou l’appel à `InvokeEx` a tenté de définir la valeur d’une propriété en lecture seule.|  
|DISP_E_NONAMEDARGS|Cette implémentation de `IDispatch` ne prend pas en charge les arguments nommés.|  
|DISP_E_OVERFLOW|Un des arguments de `rgvarg` n’a pas pu être converti vers le type spécifié.|  
|DISP_E_PARAMNOTFOUND|Un des paramètres DISPID ne correspond pas à un paramètre de la méthode.|  
|DISP_E_TYPEMISMATCH|Un ou plusieurs des arguments n’a pas pu être converti.|  
|DISP_E_UNKNOWNLCID|Le membre appelé interprète les arguments de chaîne en fonction de l’identificateur LCID, et l’identificateur LCID n’est pas reconnu. Si l’identificateur LCID n’est pas nécessaire pour interpréter les arguments, cette erreur ne doit pas être retournée.|  
|DISP_E_PARAMNOTOPTIONAL|Un paramètre obligatoire a été omis.|  
  
## <a name="example"></a>Exemple  
  
```  
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
 [IDispatchEx (Interface)](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)