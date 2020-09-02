---
title: KeyBinding, élément | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75d96098e8444aac9a4fc6f895099435b54f640b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180325"
---
# <a name="keybinding-element"></a>Élément KeyBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’élément KeyBinding spécifie les raccourcis clavier pour les commandes.  
  
 Les commandes peuvent être associées à des liaisons à clé unique et à deux clés. Un exemple de liaison de clé unique est CTRL + S pour la commande **Enregistrer** . Les combinaisons de touches doubles requièrent deux combinaisons de touches successives pour déclencher une commande. Voici un exemple de liaison à deux clés : CTRL + K, CTRL + K pour définir un signet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|guid|Obligatoire.|  
|id|Obligatoire.|  
|éditeur|Obligatoire. Le GUID de l’éditeur indique le contexte d’édition pour lequel ce raccourci clavier est actif. La valeur de portée de liaison globale est « guidVSStd97 ».|  
|key1|Obligatoire. Les valeurs valides incluent tous les alphanumériques typable, ainsi que les valeurs hexadécimales à deux chiffres précédées de 0x et VK_constants.|  
|mod1|facultatif. Toutes les combinaisons de touches CTRL, ALT et Maj sont séparées par un espace.|  
|key2|facultatif. Les valeurs valides incluent tous les alphanumériques typable, ainsi que les valeurs hexadécimales à deux chiffres précédées de 0x et VK_constants.|  
|mod2|facultatif. Toutes les combinaisons de touches CTRL, ALT et Maj sont séparées par un espace.|  
|émulateur|facultatif.|  
|Condition|facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Parent||  
|Annotation||  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément KeyBindings](../extensibility/keybindings-element.md)|Groupe les éléments KeyBinding et d’autres regroupements de combinaisons de touches.|  
  
## <a name="example"></a> Exemple  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [KeyBindings (élément)](../extensibility/keybindings-element.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
