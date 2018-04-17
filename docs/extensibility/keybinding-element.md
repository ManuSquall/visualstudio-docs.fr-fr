---
title: Élément de la combinaison de touches | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 226a5913cbaa151689a886dc88986f7de8cc29f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="keybinding-element"></a>Élément de la combinaison de touches
L’élément de la combinaison de touches Spécifie les raccourcis clavier pour les commandes.  
  
 Commandes peuvent avoir un ou deux combinaisons de touches qui s’y rapportent. Un exemple d’une liaison de clé unique est CTRL + S pour le **enregistrer** commande. Combinaisons de touches doubles nécessitent deux combinaisons de touches successives pour déclencher une commande. Un exemple d’une liaison de clé double est CTRL + K, CTRL + K pour définir un signet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|GUID|Obligatoire.|  
|ID|Obligatoire.|  
|éditeur|Obligatoire. Le GUID de l’éditeur indique le contexte d’édition pour lequel ce raccourci clavier est actif. La valeur de la portée globale de liaison est « guidVSStd97 ».|  
|key1|Obligatoire. Les valeurs valides sont peut être tapées tous les caractères alphanumériques, ainsi que les valeurs hexadécimales à deux chiffres précédés par 0 x et [VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx).|  
|MOD1|Facultatif. N’importe quelle combinaison de touches CTRL, ALT et MAJ séparés par un espace.|  
|key2|Facultatif. Les valeurs valides sont peut être tapées tous les caractères alphanumériques, ainsi que les valeurs hexadécimales à deux chiffres précédés par 0 x et [VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx).|  
|MOD2|Facultatif. N’importe quelle combinaison de touches CTRL, ALT et MAJ séparés par un espace.|  
|émulateur|Facultatif.|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Parent||  
|Annotation||  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément KeyBindings](../extensibility/keybindings-element.md)|Regroupe les éléments de combinaison de touches et autres regroupements de combinaisons de touches.|  
  
## <a name="example"></a>Exemple  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de combinaisons de touches](../extensibility/keybindings-element.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
