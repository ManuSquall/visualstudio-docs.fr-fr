---
title: "IDispatchEx, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDispatchEx (interface)"
  - "IDispatchEx (interface), à propos de IDispatchEx"
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDispatchEx, interface
`IDispatchEx`, une extension de l'interface d' `IDispatch` , fonctionnalités de charge approprié pour les langages dynamiques tels que les langages de script.  Cette section décrit l'interface d' `IDispatchEx` elle\-même, les différences entre `IDispatch` et `IDispatchEx`, et le raisonnement pour les extensions.  Supposé que les lecteurs puissent être familiarisés avec `IDispatch` et ont accès à la documentation de `IDispatch` .  
  
## Remarques  
 `IDispatch` a été développé essentiellement pour Visual Basic.  La limitation primaire d' `IDispatch` est qu'il suppose que les objets sont statiques.  En d'autres termes, étant donné que les objets ne changent pas au moment de l'exécution, les informations de type peuvent amplement les décrire au moment de la compilation.  Les modèles à l'exécution dynamiques trouvés dans les langages de script tels que Visual Basic Scripting Edition \(VBScript\) et [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] et des modèles objet tels que HTML dynamique requièrent une interface plus flexible.  
  
 `IDispatchEx` a été développé pour fournir tous les services d' `IDispatch` ainsi que de certaines extensions qui sont appropriés pour plus de langages dynamiques à liaison tardive tels que les langages de script.  Les fonctionnalités supplémentaires d' `IDispatchEx` en plus de celles fournies par `IDispatch` sont :  
  
-   Ajoutez de nouveaux membres à un objet \(« expando »\) utilisent `GetDispID` avec la balise d' `fdexNameEnsure` .  
  
-   Supprimez les membres d'un objet utilisation `DeleteMemberByName` ou `DeleteMemberByDispID`.  
  
-   Exécution\- utilisez la casse `fdexNameCaseSensitive` ou `fdexNameCaseInsensitive`d'expédition.  
  
-   Recherche du membre avec la nom\- utilisation implicite `fdexNameImplicit`.  
  
-   Énumérez les dispid d'un objet utilisation `GetNextDispID`.  
  
-   Mappage de DISPID à la nom\- utilisation `GetMemberName`d'élément.  
  
-   Obtient les propriétés de la membre utilisation `GetMemberProperties`d'objet.  
  
-   Appel de méthode avec la pointeur\-utilisation `InvokeEx` d' `this` avec DISPATCH\_METHOD.  
  
-   Autorisez les navigateurs qui prennent en charge le concept des espaces de noms pour obtenir le parent de l'espace de noms d'un objet utilisation `GetNameSpaceParent`.  
  
 Les objets qui prennent en charge `IDispatchEx` peuvent également prendre en charge `IDispatch` pour la compatibilité descendante.  La nature dynamique des objets qui prennent en charge `IDispatchEx` a des conséquences pour l'interface d' `IDispatch` de ces objets.  Par exemple, `IDispatch` fait l'hypothèse suivante :  
  
-   Le membre et le paramètre Dispid doivent rester constants pour la durée de vie de l'objet.  Cela permet à un client pour obtenir le Dispid une fois et les mettre en cache pour une utilisation ultérieure.  
  
 Étant donné qu' `IDispatchEx` permet l'ajout et la suppression des membres, l'ensemble de Dispid valide ne restent pas fixe.  Toutefois, `IDispatchEx` requiert que le mappage entre DISPID et nom du membre restent constante.  Cela signifie que si un membre est supprimé :  
  
-   Le DISPID ne peut pas être réutilisé jusqu'à ce qu'un membre portant le même nom soit créé.  
  
-   Le DISPID doit rester valide pour `GetNextDispID`.  
  
-   Le DISPID doit être accepté correctement par `IDispatch` l'un des ou `IDispatchEx` que méthode ils doivent identifier le membre comme supprimé et retourner un code d'erreur approprié \(généralement DISP\_E\_MEMBERNOTFOUND ou S\_FALSE\).  
  
## Exemples  
 Ce code d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] dans la fonction test\(\) effectue les opérations suivantes :  
  
-   Crée un objet en appelant le constructeur d' `Object` et assigne un pointeur vers le nouvel objet à Obj variable.  
  
-   Crée un élément nommé Elem dans l'objet et assigne à cet élément pointeur vers le chat de fonction.  
  
-   Appelle cette fonction.  Étant donné qu'elle est appelée comme une méthode, le pointeur d' `this` fait référence à l'objet Obj.  La fonction ajoute un nouvel élément, barre, à l'objet.  
  
 Le code HTML complet est :  
  
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
  
 Un contrôle placé sur cette même page Web peut obtenir un pointeur d'expédition aux moteurs de script du navigateur.  Le contrôle peut ensuite implémenter la fonction test\(\) :  
  
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
  
 Le code du contrôle, test, effectuez la même opération que la fonction `test()`d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  Notez que ces appels d'expédition sont transformés en moteur en cours de exécution d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] et modifier l'état du moteur :  
  
-   Obtient le pointeur d'expédition à la fonction de chat à l'aide de `GetDispID()`.  
  
-   Obtient le pointeur d'expédition à la fonction d'objet utilisant `GetDispID()`.  
  
-   Crée un objet en appelant la fonction d'objet avec `InvokeEx()` et obtient un pointeur d'expédition à l'objet nouvellement construit.  
  
-   Crée un élément, Elem, de l'objet selon `GetDispID()` avec la balise d' `fdexNameEnsure` .  
  
-   Place le pointeur d'expédition au chat dans l'élément en `InvokeEx()`.  
  
-   Appelle le pointeur d'expédition au chat comme méthode en appelant `InvokeEx()` et en passant le pointeur d'expédition à l'objet construit comme pointeur d' `this` .  
  
-   La méthode de chat crée un nouvel élément, barre, sur l'objet actuel d' `this` .  
  
-   Vérifie que le nouvel élément, barre, a été créé dans l'objet construit en énumérant via les éléments à l'aide de `GetNextDispID()`.  
  
 Le code du contrôle de test :  
  
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
  
## Méthodes  
 [IDispatchEx, méthodes](../../winscript/reference/idispatchex-methods.md)