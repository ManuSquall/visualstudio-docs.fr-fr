---
title: IDispatchEx (Interface) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 9a100a193f5e3abcb076fb8aaf3d64a0d0c38833
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24730299"
---
# <a name="idispatchex-interface"></a>IDispatchEx, interface
`IDispatchEx`, une extension de la `IDispatch` approprié à interface, les fonctionnalités de prise en charge pour les langages dynamiques tels que des langages de script. Cette section décrit la `IDispatchEx` les différences entre l’interface elle-même, `IDispatch` et `IDispatchEx`et la logique pour les extensions. Il est prévu que les lecteurs sont familiarisés avec `IDispatch` et avoir accès à la `IDispatch` documentation.  
  
## <a name="remarks"></a>Notes  
 `IDispatch`essentiellement, l’a été développé pour Microsoft Visual Basic. Le principal inconvénient de `IDispatch` est qu’elle suppose que les objets sont statiques. En d’autres termes, étant donné que les objets ne changent pas pendant l’exécution, les informations de type peuvent décrire entièrement les au moment de la compilation. Les modèles d’exécution dynamiques qui sont trouvent dans des langages tels que Visual Basic Scripting Edition (VBScript) et [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] et modèles d’objet tels que HTML dynamiques requièrent une interface plus souple.  
  
 `IDispatchEx`a été développé pour fournir tous les services de `IDispatch` , ainsi que des extensions qui sont appropriées pour les langues à liaison tardive plus dynamiques tels que des langages de script. Les fonctionnalités supplémentaires de `IDispatchEx` au-delà de celles fournies par `IDispatch` sont :  
  
-   Ajouter de nouveaux membres à un objet (« expando »), utilisez `GetDispID` avec la `fdexNameEnsure` indicateur.  
  
-   Supprimer des membres d’un objet, utilisez `DeleteMemberByName` ou `DeleteMemberByDispID`.  
  
-   Les opérations de répartition qui respecte la casse, utilisez `fdexNameCaseSensitive` ou `fdexNameCaseInsensitive`.  
  
-   Recherche d’un membre implicite portant — utilisez `fdexNameImplicit`.  
  
-   Énumérer les DISPID d’un objet, utilisez `GetNextDispID`.  
  
-   Mappage entre les DISPID et nom de l’élément, utilisez `GetMemberName`.  
  
-   Obtenir les propriétés des membres de l’objet, utilisez `GetMemberProperties`.  
  
-   L’appel de méthode avec `this` pointeur — utilisez `InvokeEx` avec DISPATCH_METHOD.  
  
-   Autoriser les navigateurs qui prennent en charge le concept d’espaces de noms pour obtenir le parent d’espace de nom d’un objet, utilisez `GetNameSpaceParent`.  
  
 Objets qui prennent en charge `IDispatchEx` peut prennent également en charge `IDispatch` pour la compatibilité descendante. La nature dynamique des objets qui prennent en charge `IDispatchEx` a certaines implications pour la `IDispatch` interface de ces objets. Par exemple, `IDispatch` part de l’hypothèse suivante :  
  
-   Le membre et le paramètre DISPID doivent rester constantes pour la durée de vie de l’objet. Cela permet au client obtenir les DISPID qu’une seule fois et de les mettre en cache pour une utilisation ultérieure.  
  
 Étant donné que `IDispatchEx` permet l’ajout et la suppression de membres, le jeu de DISPID valides n’est pas constante. Toutefois, `IDispatchEx` exige que le mappage entre les DISPID et nom de membre reste constante. Cela signifie que si un membre est supprimé :  
  
-   Le DISPID ne peut pas être réutilisé jusqu'à ce qu’un membre portant le même nom est créé.  
  
-   Le DISPID doit rester valide pour `GetNextDispID`.  
  
-   Le DISPID doit être accepté normalement par un de la `IDispatch` ou `IDispatchEx` méthodes, ils doivent reconnaître le membre comme étant supprimé et retourner un code d’erreur approprié (généralement DISP_E_MEMBERNOTFOUND ou S_FALSE).  
  
## <a name="examples"></a>Exemples  
 Cela [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] code dans la fonction test() effectue les opérations suivantes :  
  
-   Crée un objet en appelant le `Object` constructeur et assigne un pointeur vers le nouvel objet à l’objet de variable.  
  
-   Crée un élément nommé Elem dans l’objet et l’assigne à cet élément, un pointeur vers la cat (fonction).  
  
-   Appelle cette fonction. Dans la mesure où il est appelé en tant que méthode, la `this` pointeur fait référence à l’objet obj. La fonction ajoute un nouvel élément, barre, à l’objet.  
  
 Le code HTML complet est la suivante :  
  
```  
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
  
 Un contrôle placé sur la même page Web peut obtenir un pointeur de répartition pour les moteurs de script à partir du navigateur. Le contrôle peut ensuite implémenter la fonction test() :  
  
```  
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
  
 À partir du contrôle de code, tester, produit la même chose que le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fonction `test()`. Notez que ces appels de distribution sont transformés en l’exécutant [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] moteur et de modifier l’état du moteur :  
  
-   Obtient le pointeur de dispatch pour la fonction cat en utilisant `GetDispID()`.  
  
-   Obtient le pointeur de dispatch pour la fonction d’objet à l’aide `GetDispID()`.  
  
-   Construit un objet en appelant la fonction de l’objet avec `InvokeEx()` et obtient un pointeur de dispatch vers l’objet qui vient d’être construit.  
  
-   Crée un nouvel élément, Elem, dans l’objet en utilisant `GetDispID()` avec la `fdexNameEnsure` indicateur.  
  
-   Place le pointeur de la répartition par cat dans l’élément à l’aide de `InvokeEx()`.  
  
-   Appelle le pointeur de la répartition par cat en tant que méthode en appelant `InvokeEx()` et en passant le pointeur de répartition à l’objet construit en tant que le `this` pointeur.  
  
-   La méthode cat crée un nouvel élément, barre, dans le courant `this` objet.  
  
-   Vérifie que le nouvel élément, à barres, a été créé dans l’objet construit par les éléments à l’aide de l’énumération `GetNextDispID()`.  
  
 Le code pour le contrôle de test :  
  
```  
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