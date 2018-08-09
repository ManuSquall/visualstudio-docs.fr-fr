---
title: Élément KeyBinding | Microsoft Docs
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
ms.openlocfilehash: 3b5e35738f04dd4a05a753a58e91ca385ecd56bd
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639322"
---
# <a name="keybinding-element"></a>Élément KeyBinding
L’élément de combinaison de touches Spécifie les raccourcis clavier pour les commandes.  
  
 Commandes peuvent avoir un ou deux combinaisons de touches qui s’y rapportent. Est un exemple d’une liaison de clé unique **Ctrl**+**S** pour le **enregistrer** commande. Les combinaisons de touches doubles nécessitent deux combinaisons de touches successives pour déclencher une commande. Est un exemple d’une combinaison de touches double **Ctrl * +** K **,** Ctrl**+** K ** pour définir un signet.  
  
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
|key1|Obligatoire. Les valeurs valides incluent peut être tapées tous les caractères alphanumériques et les valeurs hexadécimales à deux chiffres précédés par 0 x et [VK_constants](https://msdn.microsoft.com/library/windows/desktop/dd375731.aspx).|  
|MOD1|Facultatif. N’importe quelle combinaison de **Ctrl**, **Alt**, et **MAJ** séparés par un espace.|  
|key2|Facultatif. Les valeurs valides incluent peut être tapées tous les caractères alphanumériques et les valeurs hexadécimales à deux chiffres précédés par 0 x et [VK_constants](https://msdn.microsoft.com/library/windows/desktop/dd375731.aspx).|  
|MOD2|Facultatif. N’importe quelle combinaison de **Ctrl**, **Alt**, et **MAJ** séparés par un espace.|  
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
 [Visual Studio fichiers command table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
