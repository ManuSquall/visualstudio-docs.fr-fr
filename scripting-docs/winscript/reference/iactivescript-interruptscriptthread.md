---
title: "IActiveScript::InterruptScriptThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.InterruptScriptThread
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_InterruptScriptThread"
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::InterruptScriptThread
Interrompt l'exécution d'un thread en cours de exécution du script \(un récepteur d'événements, une exécution immédiate, ou un appel de macro\).  Cette méthode peut être utilisée pour exécuter un script qui est coincé \(par exemple, dans une boucle infinie\).  Elle peut être appelée des threads non base sans ce qui provoque une légende non base des objets hôte ou à la méthode d' [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## Syntaxe  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### Paramètres  
 `stidThread`  
 \[in\]  L'identificateur du thread à abandonner, ou l'un de l'identificateur spécial suivant de thread a :  
  
|Valeur|Signification|  
|------------|-------------------|  
|SCRIPTTHREADID\_ALL|Tous les threads.  L'interruption s'applique à toutes les méthodes de script en cours.  Notez qu'à moins que l'appelant l'a demandé que le script est déconnecté, suivant le code de script de script causes d'événements d'exécuter à nouveau en appelant la méthode d' [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) avec la valeur de la balise de SCRIPTSTATE\_DISCONNECTED ou de SCRIPTSTATE\_INITIALIZED.|  
|SCRIPTTHREADID\_BASE|Le thread de base ; autrement dit, le thread dans lequel le moteur de script a été instancié.|  
|SCRIPTTHREADID\_CURRENT|Le thread en cours.|  
  
 `pexcepinfo`  
 \[in\]  Adresse d'une structure d' `EXCEPINFO` contenant des informations d'erreur qui doivent être inscrits au script suspendu.  
  
 `dwFlags`  
 \[in\]  Balises d'option associées à l'interruption.  Il peut s'agir de l'une des valeurs suivantes :  
  
|Valeur|Signification|  
|------------|-------------------|  
|SCRIPTINTERRUPT\_DEBUG|Si pris en charge, entrez le débogueur du moteur de script à le point actuel d'exécution du script.|  
|SCRIPTINTERRUPT\_RAISEEXCEPTION|Si pris en charge par le langage du moteur de script, laissez le script gérer l'exception.  Sinon, la méthode de script est interrompue et code d'erreur est retourné à l'appelant ; autrement dit, le demandeur source de l'événement ou de macro.|  
  
## Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|Valeur de retour|Signification|  
|----------------------|-------------------|  
|`S_OK`|Succès.|  
|`E_INVALIDARG`|Un argument n'était pas valide.|  
|`E_POINTER`|Un pointeur non valide a été spécifié.|  
|`E_UNEXPECTED`|L'appel à n'a pas été conçu \(par exemple, le moteur de script n'a pas encore été chargé ou n'a pas été initialisé.\)|  
  
## Voir aussi  
 [IActiveScript](../../winscript/reference/iactivescript.md)