---
title: "&#201;l&#233;ment de bouton | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Élément de boutons (schéma XML de VSCT)"
  - "Éléments du schéma XML de VSCT, boutons"
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# &#201;l&#233;ment de bouton
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Définit un élément que l’utilisateur peut interagir avec. Boutons peuvent être de différents types : bouton, bouton de menu et SplitDropDown.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|GUID|Obligatoire. GUID de l’identificateur de commande/ID GUID.|  
|ID|Obligatoire. ID de l’identificateur de commande/ID GUID.|  
|priority|Facultatif. Une valeur numérique qui spécifie la priorité.|  
|type|Facultatif. Valeur énumérée qui spécifie le type de bouton.<br /><br /> Si non, utilise le bouton.<br /><br /> Bouton<br /> Une commande standard qui apparaît sur les barres d’outils (en général comme un bouton sous forme d’icône), menus et menus contextuels.<br /><br /> Bouton de menu<br /> Un élément de menu qui n’exécute pas une commande, mais génère un autre menu.<br /><br /> SplitDropDown<br /> Contrôles, tels que les boutons Annuler et rétablir la barre d’outils standard dans Microsoft Word.|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément parent](../extensibility/parent-element.md)|Facultatif. L’élément parent du bouton.|  
|[Icon, élément](../extensibility/icon-element.md)|Facultatif. L’icône associée au bouton.|  
|[Élément indicateur de commande](../extensibility/command-flag-element.md)|Obligatoire. Voici les valeurs CommandFlag valides pour un bouton.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TexteModifie<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Élément de chaînes](../extensibility/strings-element.md)|Obligatoire. L’enfant [ButtonText élément](../extensibility/buttontext-element.md) doit être défini.|  
|Annotation|Commentaire facultatif.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de boutons](../extensibility/buttons-element.md)|Regroupe les éléments de bouton.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit un bouton dans un fichier .vsct.  
  
 [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]  
  
## <a name="see-also"></a>Voir aussi  
 [Table de commandes de Visual Studio (. Fichiers VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)