---
title: "&#201;l&#233;ment de KeyBinding | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Éléments du schéma XML de VSCT, thèmes"
  - "KeyBinding, élément (schéma XML de VSCT)"
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# &#201;l&#233;ment de KeyBinding
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'élément KeyBinding indique les raccourcis clavier des commandes.  
  
 Commandes peuvent avoir un ou deux combinaisons de touches associées. Un exemple d'une liaison de clé unique est CTRL \+ S pour le **Enregistrer** commande. Les combinaisons de touches doubles nécessitent deux combinaisons de touches successives pour déclencher une commande. Un exemple d'une liaison de clé double est CTRL \+ K,CTRL \+ K pour définir un signet.  
  
## Syntaxe  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|GUID|Obligatoire.|  
|ID|Obligatoire.|  
|éditeur|Obligatoire. L'éditeur de GUID indique le contexte d'édition pour lequel ce raccourci clavier est actif. La valeur de la portée globale de liaison est « guidVSStd97 ».|  
|Key1|Obligatoire. Les valeurs valides incluent tous les caractères alphanumériques peut être tapée, ainsi que les valeurs hexadécimales à deux chiffres précédés par 0 x et VK\_constants.|  
|MOD1|Facultatif. N'importe quelle combinaison de touches CTRL, ALT et MAJ séparés par un espace.|  
|Key2|Facultatif. Les valeurs valides incluent tous les caractères alphanumériques peut être tapée, ainsi que les valeurs hexadécimales à deux chiffres précédés par 0 x et VK\_constants.|  
|MOD2|Facultatif. N'importe quelle combinaison de touches CTRL, ALT et MAJ séparés par un espace.|  
|émulateur|Facultatif.|  
|Condition|Facultatif. Consultez [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Parent||  
|Annotation||  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de thèmes](../extensibility/keybindings-element.md)|Regroupe les éléments KeyBinding et autres regroupements de thèmes.|  
  
## Exemple  
  
```  
<KeyBindings> <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget" editor="guidWidgetEditor" key1="VK_F5"/> <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget" editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/> </KeyBindings>  
```  
  
## Voir aussi  
 [Élément de thèmes](../extensibility/keybindings-element.md)   
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)