---
title: Interface IDispatchEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df3fd7d46fdcb1f3e86bddd53700d7bce6e21381
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145250"
---
# <a name="idispatchex-interface"></a>IDispatchEx, interface
`IDispatchEx`, une extension de la `IDispatch` interface, des fonctionnalités de prise en charge appropriées pour les langages dynamiques tels que des langages de script. Cette section décrit la `IDispatchEx` les différences entre l’interface proprement dite, `IDispatch` et `IDispatchEx`et la logique pour les extensions. Il est probable que les lecteurs sont familiers avec `IDispatch` et ont accès à la `IDispatch` documentation.  
  
## <a name="remarks"></a>Notes  
 `IDispatch` essentiellement, l’a été développé pour Microsoft Visual Basic. La principale limitation de `IDispatch` est qu’elle suppose que les objets sont statiques. En d’autres termes, dans la mesure où les objets ne changent pas pendant l’exécution, les informations de type peuvent se décrire complètement les au moment de la compilation. Modèles d’exécution dynamiques qui sont trouvent dans des langages de script tels que Visual Basic Scripting Edition (VBScript) et [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] et modèles d’objet, telles que HTML dynamique nécessiter une interface plus souple.  
  
 `IDispatchEx` a été développé pour fournir tous les services de `IDispatch` , ainsi que certaines extensions qui conviennent à des langages à liaison tardive plus dynamiques tels que des langages de script. Les fonctionnalités supplémentaires du `IDispatchEx` au-delà de celles fournies par `IDispatch` sont :  
  
- Ajouter de nouveaux membres à un objet (« expando »), utilisez `GetDispID` avec la `fdexNameEnsure` indicateur.  
  
- Supprimer des membres d’un objet, utilisez `DeleteMemberByName` ou `DeleteMemberByDispID`.  
  
- Opérations de répartition de la casse, utilisez `fdexNameCaseSensitive` ou `fdexNameCaseInsensitive`.  
  
- Recherchez le membre nom implicite — utilisez `fdexNameImplicit`.  
  
- Énumérer les DISPID d’un objet, utilisez `GetNextDispID`.  
  
- Mappage entre les DISPID et nom de l’élément, utilisez `GetMemberName`.  
  
- Obtenir les propriétés de membres de l’objet, utilisez `GetMemberProperties`.  
  
- Appel de méthode avec `this` pointeur — utilisez `InvokeEx` avec DISPATCH_METHOD.  
  
- Autoriser les navigateurs qui prennent en charge le concept d’espaces de noms pour obtenir le parent d’espace de nom d’un objet, utilisez `GetNameSpaceParent`.  
  
  Objets qui prennent en charge `IDispatchEx` peut également prendre en charge `IDispatch` pour la compatibilité descendante. La nature dynamique des objets qui prennent en charge `IDispatchEx` a quelques implications pour le `IDispatch` interface de ces objets. Par exemple, `IDispatch` part de l’hypothèse suivante :  
  
- Le membre et le paramètre DISPID doit rester constante pour la durée de vie de l’objet. Cela permet au client obtenir le DISPID qu’une seule fois et de les mettre en cache pour une utilisation ultérieure.  
  
  Dans la mesure où `IDispatchEx` permet l’ajout et la suppression de membres, l’ensemble de DISPID valide n’est pas constante. Toutefois, `IDispatchEx` exige que le mappage entre les DISPID et nom de membre reste constante. Cela signifie que si un membre est supprimé :  
  
- Le DISPID ne peut pas être réutilisé jusqu'à ce qu’un membre portant le même nom est créé.  
  
- Le DISPID doit rester valide pour `GetNextDispID`.  
  
- Le DISPID doit être accepté normalement en fonction des différentes le `IDispatch` ou `IDispatchEx` méthodes, ils doivent reconnaître le membre comme étant supprimé et retourner un code d’erreur approprié (généralement DISP_E_MEMBERNOTFOUND ou S_FALSE).  
  
## <a name="examples"></a>Exemples  
 Cela [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] code dans la fonction test() effectue les opérations suivantes :  
  
- Crée un objet en appelant le `Object` constructeur et assigne un pointeur vers le nouvel objet à l’objet variable.  
  
- Crée un nouvel élément nommé Elem dans l’objet et attribue à cet élément, un pointeur vers le Chat (fonction).  
  
- Appelle cette fonction. Dans la mesure où elle est appelée en tant que méthode, la `this` pointeur fait référence à l’objet obj. La fonction ajoute un nouvel élément, barre, à l’objet.  
  
  Le code HTML complet est :  
  
```html
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 Un contrôle placé sur cette même page Web peut obtenir un pointeur dispatch pour les moteurs de script à partir du navigateur. Le contrôle peut ensuite implémenter la fonction test() :  
  
```html
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 À partir du contrôle de code, de test, de fait la même chose que le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fonction `test()`. Notez que ces appels de distribution sont transformés en l’exécutant [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur et de modifier l’état du moteur :  
  
- Obtient le pointeur dispatch vers l’à l’aide de la fonction de cat `GetDispID()`.  
  
- Obtient le pointeur dispatch vers l’objet fonction en utilisant `GetDispID()`.  
  
- Construit un objet en appelant la fonction de l’objet avec `InvokeEx()` et obtient un pointeur dispatch vers l’objet nouvellement construit.  
  
- Crée un nouvel élément, Elem, dans l’objet en utilisant `GetDispID()` avec la `fdexNameEnsure` indicateur.  
  
- Place le pointeur de la répartition par cat dans l’élément à l’aide `InvokeEx()`.  
  
- Appelle le pointeur dispatch vers cat en tant que méthode en appelant `InvokeEx()` et en passant le pointeur dispatch vers l’objet construit en tant que le `this` pointeur.  
  
- La méthode cat crée un nouvel élément, la barre, dans le cours `this` objet.  
  
- Vérifie que le nouvel élément, à barres, a été créé dans l’objet construit par énumérer les éléments à l’aide de `GetNextDispID()`.  
  
  Le code pour le contrôle de test :  
  
```cpp
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>Méthodes  
 [Méthodes IDispatchEx](../../winscript/reference/idispatchex-methods.md)