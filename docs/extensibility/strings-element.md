---
title: "Chaînes d’élément | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 86e0148d495914b1cb1c0f0d19125992930a9521
ms.lasthandoff: 02/22/2017

---
# <a name="strings-element"></a>Élément de chaînes
L’élément de chaînes doit contenir au moins un **ButtonText** élément enfant. Tous les autres éléments enfants sont facultatifs. Comme les caractères XML non valide '<' et '<’ must="" be="" coded="" as="" entities=""></’>&amp;'et'&lt;» et ainsi de suite).  
  
 Un « et commercial » dans la chaîne de texte spécifie le raccourci clavier de la commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Strings>  
  <ButtonText>... </ButtonText>  
  <CommandName>... </CommandName>  
</Strings>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|language|Facultatif. Language = «. ».|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|ButtonText|Ce champ et les cinq champs de texte suivantes dans une définition de commande vous permettent de spécifier le texte qui apparaît dans les différents menus. Par défaut, le `ButtonText` champ s’affiche dans les contrôleurs de menu. Le `ButtonText` champ devient également la valeur par défaut si les autres champs de texte sont vides. Le `ButtonText` champ ne peut pas être vide même si les autres champs de texte sont spécifiées.|  
|ToolTipText|Le `ToolTipText` champ spécifie le texte qui apparaît dans l’info-bulle pour un élément de menu.<br /><br /> Si le `ToolTipText` champ est vide, le `ButtonText` champ est utilisé.|  
|MenuText|Le `MenuText` champ spécifie le texte qui s’affiche pour une commande si elle se trouve sur le menu principal, une barre d’outils, dans un menu contextuel ou un sous-menu. Si le `MenuText` champ est vide, l’environnement de développement intégré (IDE) utilise le `ButtonText` champ. Le `MenuText` champ peut également être utilisé pour la localisation.<br /><br /> Pour les menus contextuels, les `MenuText` champ est le nom qui s’affiche dans la barre d’outils Menus contextuels, qui permet la personnalisation des menus contextuels dans l’IDE. Par conséquent, être spécifique dans ce que vous nommez votre menu contextuel ; par exemple, utilisez « Menu contextuel Widget Package » au lieu de « Raccourci ».<br /><br /> Si le `MenuText` champ n’est pas spécifié, le `ButtonText` champ est utilisé.|  
|CommandName|Le `CommandName` champ spécifie le texte qui apparaît dans la catégorie de clavier dans le **commandes** onglet dans le **personnaliser** boîte de dialogue (disponible en cliquant sur **personnaliser** sur la **outils** menu).|  
|CanonicalName|L’anglais `CanonicalName` champ spécifie le nom de la commande de texte en anglais qui peut être entré dans le **commande** fenêtre pour exécuter l’élément de menu. L’IDE supprime tous les caractères qui ne sont pas des lettres, chiffres, des traits de soulignement ou des points incorporés. Ce texte est ensuite concaténé à la `ButtonText` champ pour définir la commande. Par exemple, **nouveau projet** sur la **fichier** menu devient la commande File.NewProject.<br /><br /> Si l’anglais `CanonicalName` champ n’est pas spécifié, l’IDE utilise le `ButtonText` champ et bandes tous à l’exception des lettres, des chiffres, des traits de soulignement et des points incorporés. Par exemple, le texte du bouton « se définir commandes... » devient DefineCommands, où le signe &, l’espace et les points de suspension sont supprimés.<br /><br /> Si le `TextChanges` indicateur est spécifié et le texte de la commande est modifié, la commande correspondante est reconnue par le **commande** fenêtre ne modifie pas, il reste la forme canonique de l’original `ButtonText` ou anglais `CanonicalName` champs.|  
|LocCanonicalName|Le `LocCanonicalName` champ se comporte comme l’anglais `CanonicalName` champ mais permet de texte de commande localisée à être spécifié. Les deux champs canoniques peuvent être spécifiés. Étant donné que l’IDE analyse uniquement le texte entré dans le **commande** fenêtre et l’associe à une commande, l’anglais et non anglophones texte peut être associé à la même commande.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de bouton](../extensibility/button-element.md)|Définit un élément que l’utilisateur peut interagir avec.|  
|[Élément de menu](../extensibility/menu-element.md)|Définit un seul élément de menu.|  
|[Élément de liste déroulante](../extensibility/combo-element.md)|Définit des commandes qui s’affichent dans une zone de liste déroulante.|  
  
## <a name="see-also"></a>Voir aussi  
 [Table de commandes de Visual Studio (. Fichiers VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
