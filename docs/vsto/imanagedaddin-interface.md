---
title: "Interface IManagedAddin | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "interface IManagedAddin"
ms.assetid: 5350629c-6cf8-42dd-ae65-3f34322ee10f
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Interface IManagedAddin
  Implémentez l’interface IManagedAddin pour créer un composant qui charge des compléments VSTO gérés. Cette interface a été ajoutée dans la version 2007 de Microsoft Office System.  
  
## Syntaxe  
  
```  
[  
    object,  
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),  
    pointer_default(unique),  
    oleautomation  
]  
interface IManagedAddin : IUnknown  
{  
    HRESULT Load(  
        [in] BSTR bstrManifestURL,   
        [in] IDispatch *pdispApplication);  
    HRESULT Unload();  
};  
```  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes définies par l’interface IManagedAddin.  
  
|Nom|Description|  
|---------|-----------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Appelée quand une application Microsoft Office charge un complément VSTO géré.|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Appelée juste avant qu’une application Microsoft Office décharge un complément VSTO géré.|  
  
## Notes  
 Les applications Microsoft Office, depuis la version 2007 de Microsoft Office System, utilisent l’interface IManagedAddin pour charger des compléments VSTO Office. Vous pouvez implémenter l’interface IManagedAddin pour créer vos propres chargeur et runtime de complément VSTO pour les compléments VSTO gérés, au lieu d’utiliser le chargeur de complément VSTO \(VSTOLoader.dll\) et [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Pour plus d'informations, consultez [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
## Mode de chargement des compléments gérés  
 Les étapes suivantes se produisent au démarrage d’une application :  
  
1.  L’application découvre les compléments VSTO en recherchant des entrées sous la clé de Registre suivante :  
  
     HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<nom\_application\>*\\Addins\\  
  
     Chaque entrée sous cette clé de Registre est un ID unique du complément VSTO. En règle générale, il s’agit du nom de l’assembly du complément VSTO.  
  
2.  L’application cherche une entrée `Manifest` sous l’entrée de chaque complément VSTO.  
  
     Les compléments VSTO gérés peuvent stocker le chemin complet d’un manifeste dans l’entrée `Manifest` sous HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<nom\_application\>*\\Addins\\*\<ID\_complément\>*. Un manifeste est un fichier \(en général, un fichier XML\) qui fournit des informations qui sont utilisées pour charger le complément VSTO.  
  
3.  Si l’application trouve une entrée `Manifest`, elle essaie de charger un composant de chargeur de complément VSTO géré. Pour cela, l’application essaie de créer un objet COM qui implémente l’interface IManagedAddin.  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] inclut un composant de chargeur de complément VSTO \(VSTOLoader.dll\). Vous pouvez aussi créer le vôtre en implémentant l’interface IManagedAddin.  
  
4.  L’application appelle la méthode [IManagedAddin::Load](../vsto/imanagedaddin-load.md) et passe la valeur de l’entrée `Manifest`.  
  
5.  La méthode [IManagedAddin::Load](../vsto/imanagedaddin-load.md) effectue les tâches requises pour charger le complément VSTO, notamment la configuration du domaine d’application et de la stratégie de sécurité pour le complément VSTO chargé.  
  
 Pour plus d’informations sur les clés de Registre que les applications Microsoft utilisent pour découvrir et charger des compléments VSTO gérés, consultez [Entrées de Registre pour les compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## Instructions pour l’implémentation d’IManagedAddin  
 Si vous implémentez IManagedAddin, vous devez inscrire la DLL qui contient l’implémentation à l’aide du CLSID suivant :  
  
 99D651D7\-5F7C\-470E\-8A3B\-774D5D9536AC  
  
 Les applications Microsoft Office utilisent ce CLSID pour créer l’objet COM qui implémente IManagedAddin.  
  
> [!CAUTION]  
>  Ce CLSID est également utilisé par VSTOLoader.dll dans [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Ainsi, si vous utilisez IManagedAddin pour créer votre propre composant de chargeur et d’exécution de complément VSTO, vous ne pouvez pas déployer votre composant sur des ordinateurs qui exécutent des compléments VSTO qui s’appuient sur [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## Voir aussi  
 [Référence des API non managées &#40;Développement Office dans Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  