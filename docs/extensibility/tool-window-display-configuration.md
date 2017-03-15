---
title: "Outil de Configuration de l’affichage fenêtre | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 8
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
ms.openlocfilehash: 9478ffb6ffc1fcd2204065ff4fb7cb113ab88ba4
ms.lasthandoff: 02/22/2017

---
# <a name="tool-window-display-configuration"></a>Configuration de l’affichage fenêtre outil
Lorsqu’un VSPackage enregistre une fenêtre outil, la position par défaut, taille, le style d’ancrage et autres informations sur la visibilité est spécifié dans les valeurs facultatives. Pour plus d’informations sur l’inscription de la fenêtre outil, consultez [fenêtres Outil dans le Registre](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Informations sur la fenêtre Affichage  
 Configuration de l’affichage de base d’une fenêtre outil est stockée dans les six valeurs facultatives :  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|Nom|Type|Données|Description|  
|----------|----------|----------|-----------------|  
|Nom|REG_SZ|« Nom court s’affiche ici »|Un nom court qui décrit la fenêtre outil. Utilisé uniquement pour la référence dans le Registre.|  
|Float|REG_SZ|« X1, Y1, X2, Y2 »|Quatre valeurs séparées par des virgules. X1, Y1 est la coordonnée de l’angle supérieur gauche de la fenêtre outil. X2, Y2 est la coordonnée de l’angle inférieur droit. Toutes les valeurs sont en coordonnées d’écran.|  
|Style|REG_SZ|« MDI »<br /><br /> « Flotter »<br /><br /> « Liés »<br /><br /> « Onglets »<br /><br /> « AlwaysFloat »|Un mot clé spécifiant la première affiche l’état de la fenêtre outil.<br /><br /> « MDI » = ancrée à la fenêtre MDI.<br /><br /> « Flotter » = flottant.<br /><br /> « Liés » = liée à une autre fenêtre (spécifiée dans l’entrée de la fenêtre).<br /><br /> « Onglets » = combinée avec une autre fenêtre outil.<br /><br /> « AlwaysFloat » = ne peut pas être ancré.<br /><br /> Pour plus d’informations, consultez la section commentaires ci-dessous.|  
|Fenêtre|REG_SZ|*\<GUID >*|Le GUID d’une fenêtre à laquelle la fenêtre outil peut être liée ou à onglets. Le GUID peut appartenir à un de vos propres fenêtres ou de windows dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE.|  
|Orientation|REG_SZ|« Gauche »<br /><br /> « Droite »<br /><br /> « Top »<br /><br /> « Bas »|Consultez la section commentaires ci-dessous.|  
|DontForceCreate|REG_DWORD|0 ou 1|Lorsque cette entrée est présente et que sa valeur n’est pas égal à zéro, la fenêtre est chargée, mais s’affiche pas immédiatement.|  
  
### <a name="comments"></a>Commentaires  
 L’entrée de l’Orientation définit la position où la fenêtre outil ancre lorsque l’utilisateur double-clique sur la barre de titre. La position est relatif à la fenêtre spécifiée dans l’entrée de la fenêtre. Si l’entrée de Style est définie sur « Lié », l’entrée de l’Orientation peut être « Gauche », « Droite », « Top » ou « Bas ». Si l’entrée de Style est par « onglets », l’orientation de l’entrée peut être « gauche » ou « Right » et spécifie où l’onglet est ajouté. Si l’entrée de Style est « Flotter », la fenêtre Outil flotte tout d’abord. Lorsque vous double-cliquez sur la barre de titre, les entrées de l’Orientation et la fenêtre s’appliquent, et la fenêtre utilise le style avec « onglets ». Si l’entrée de Style est « AlwaysFloat », la fenêtre outil ne peut pas être ancrée. Si l’entrée de Style est « MDI », la fenêtre outil est liée à la zone MDI, et l’entrée est ignorée.  
  
### <a name="example"></a>Exemple  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>Visibilité de la fenêtre outil  
 Valeurs dans la sous-clé de visibilité facultatif déterminent les paramètres de visibilité d’une fenêtre outil. Les noms des valeurs sont utilisés pour stocker les GUID des commandes qui requièrent une visibilité de la fenêtre. Si la commande est exécutée, l’IDE garantit que la fenêtre outil est créée et rendue visible.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|Nom|Type|Données|Description|  
|----------|----------|----------|-----------------|  
|(Default)|REG_SZ|Aucun|Laissez vide.|  
|*\<GUID >*|REG_DWORD ou REG_SZ|0 ou une chaîne descriptive.|Facultatif. Nom de l’entrée doit être le GUID d’une commande nécessitant une visibilité. La valeur conserve seulement une chaîne informative. En règle générale, la valeur est un `reg_dword` définie sur 0.|  
  
### <a name="example"></a>Exemple  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de base des VSPackages](../misc/vspackage-essentials.md)
