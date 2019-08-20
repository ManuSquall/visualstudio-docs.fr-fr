---
title: Chaînes d’élément | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0eae2fd7490269d713beb9950163071dd3ba32f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160569"
---
# <a name="strings-element"></a>Élément Strings
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’élément de chaînes doit contenir au moins un **ButtonText** élément enfant. Tous les autres éléments enfants sont facultatifs. Des caractères XML non valide, tel que '&' et ' <' doivent être codés en tant qu’entités ('&amp;« et »&lt;» et ainsi de suite).  
  
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
|langage|facultatif. Language = «. ».|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|ButtonText|Ce champ et les cinq champs de texte suivantes dans une définition de commande vous permettent de spécifier le texte qui apparaît dans différents menus. Par défaut, le `ButtonText` champ s’affiche dans les contrôleurs de menu. Le `ButtonText` champ devient également la valeur par défaut si les autres champs de texte sont vides. Le `ButtonText` champ ne peut pas être vide, même si les autres champs de texte sont spécifiées.|  
|ToolTipText|Le `ToolTipText` champ spécifie le texte qui apparaît dans l’info-bulle pour un élément de menu.<br /><br /> Si le `ToolTipText` champ est vide, le `ButtonText` champ est utilisé.|  
|MenuText|Le `MenuText` champ spécifie le texte qui est affiché pour une commande si elle est dans le menu principal, une barre d’outils dans un menu contextuel, ou dans un sous-menu. Si le `MenuText` champ est vide, l’environnement de développement intégré (IDE) utilise le `ButtonText` champ. Le `MenuText` champ peut également être utilisé pour la localisation.<br /><br /> Pour les menus contextuels, la `MenuText` champ est le nom qui s’affiche dans la barre d’outils de Menus contextuels, qui permet la personnalisation des menus contextuels dans l’IDE. Par conséquent, être spécifique dans ce que vous nommez votre menu contextuel ; par exemple, utilisez « Menu contextuel Widget Package » au lieu de « Raccourci ».<br /><br /> Si le `MenuText` champ n’est pas spécifié, le `ButtonText` champ est utilisé.|  
|CommandName|Le `CommandName` champ spécifie le texte qui apparaît dans la catégorie de clavier dans le **commandes** onglet dans le **personnaliser** boîte de dialogue (disponible en cliquant sur **personnaliser**sur le **outils** menu).|  
|CanonicalName|L’anglais `CanonicalName` champ spécifie le nom de la commande dans le texte en anglais qui peut être entré dans le **commande** fenêtre pour exécuter l’élément de menu. L’IDE supprime tous les caractères qui ne sont pas des lettres, chiffres, des traits de soulignement ou des points incorporés. Ce texte est ensuite concaténé à le `ButtonText` champ pour définir la commande. Par exemple, **nouveau projet** sur le **fichier** menu devient la commande, File.NewProject.<br /><br /> Si l’anglais `CanonicalName` champ n’est pas spécifié, l’IDE utilise le `ButtonText` champ et les bandes tous à l’exception des lettres, des chiffres, des traits de soulignement et des points incorporés. Par exemple, le texte du bouton « & définir des commandes... » devient DefineCommands, où le signe &, l’espace et les points de suspension sont supprimées.<br /><br /> Si le `TextChanges` indicateur est spécifié et le texte de la commande est modifié, la commande correspondante reconnue par le **commande** fenêtre ne change pas ; il reste de la forme canonique de la version d’origine `ButtonText` ou anglais `CanonicalName` champs.|  
|LocCanonicalName|Le `LocCanonicalName` champ se comporte comme l’anglais `CanonicalName` champ mais permet de texte de commande localisée à être spécifié. Les deux champs canoniques peuvent être spécifiés. Étant donné que l’IDE analyse simplement le texte entré dans le **commande** fenêtre et l’associe à une commande, l’anglais et non anglaises texte peut être associé à la même commande.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Button](../extensibility/button-element.md)|Définit un élément de l’utilisateur peut interagir avec.|  
|[Élément Menu](../extensibility/menu-element.md)|Définit un élément de menu unique.|  
|[Élément Combo](../extensibility/combo-element.md)|Définit des commandes qui s’affichent dans une zone de liste déroulante.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
