---
title: Élément KeyBinding | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 144d9afa3b29cd5ecebd2e3c1d604b88ba0a7029
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829155"
---
# <a name="keybinding-element"></a>Élément KeyBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’élément de combinaison de touches Spécifie les raccourcis clavier pour les commandes.  
  
 Commandes peuvent avoir un ou deux combinaisons de touches qui s’y rapportent. Un exemple d’une liaison de clé unique est CTRL + S pour le **enregistrer** commande. Les combinaisons de touches doubles nécessitent deux combinaisons de touches successives pour déclencher une commande. Un exemple d’une liaison de clé double est CTRL + K, CTRL + K pour définir un signet.  
  
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
|éditeur|Obligatoire. Le GUID de l’éditeur indique le contexte d’édition pour laquelle ce raccourci clavier est actif. La valeur d’étendue globale de liaison est « guidVSStd97 ».|  
|key1|Obligatoire. Les valeurs valides incluent tous les caractères d’alphanumériques peut être tapée et également les valeurs hexadécimales à deux chiffres précédés par 0 x et VK_constants.|  
|MOD1|Facultatif. N’importe quelle combinaison de touches CTRL, ALT et MAJ séparés par un espace.|  
|key2|Facultatif. Les valeurs valides incluent tous les caractères d’alphanumériques peut être tapée et également les valeurs hexadécimales à deux chiffres précédés par 0 x et VK_constants.|  
|MOD2|Facultatif. N’importe quelle combinaison de touches CTRL, ALT et MAJ séparés par un espace.|  
|Émulateur|Facultatif.|  
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
 [Élément KeyBindings](../extensibility/keybindings-element.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

