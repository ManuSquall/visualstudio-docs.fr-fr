---
title: "IManagedAddin::Load | Microsoft Docs"
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
  - "IManagedAddin::Load"
  - "Load (méthode)"
ms.assetid: 3faf9312-8ab4-4960-b2e7-8ca9859a3dcf
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# IManagedAddin::Load
  Appelée quand un complément VSTO managé est chargé.  
  
## Syntaxe  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*bstrManifestURL*|Chemin d’accès complet du manifeste du complément VSTO.|  
|*pdispApplication*|Pointeur vers un IDispatch qui représente l’application hôte qui charge le complément VSTO.|  
  
## Valeur de retour  
 Valeur HRESULT qui indique si la méthode a réussi.  
  
## Notes  
 Un manifeste est un fichier \(en général un fichier XML\) qui fournit des informations utilisées pour aider à charger le complément VSTO. Par exemple, un manifeste peut spécifier l’emplacement de l’assembly du complément VSTO et la classe de point d’entrée à instancier lors du chargement du complément VSTO.  
  
 Le paramètre *bstrManifestURL* contient la valeur de l’entrée `Manifest` sous la clé de Registre HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<nom\_application\>*\\Addins\\*\<ID\_complément\>* pour le complément VSTO. Pour plus d'informations, consultez [Interface IManagedAddin](../vsto/imanagedaddin-interface.md).  
  
 Implémentez la méthode [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) pour effectuer des tâches telles que la configuration de la stratégie de sécurité et du domaine d’application pour le complément VSTO chargé.  
  
## Voir aussi  
 [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  