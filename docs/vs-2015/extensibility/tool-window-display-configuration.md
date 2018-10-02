---
title: Outil de Configuration de la fenêtre Affichage | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ff1e5b95b684c347ee1885d5dfddeb5eebb5a82
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507142"
---
# <a name="tool-window-display-configuration"></a>Configuration de l’affichage fenêtre outil
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [affichage Configuration de la fenêtre outil](https://docs.microsoft.com/visualstudio/extensibility/tool-window-display-configuration).  
  
Quand un VSPackage enregistre une fenêtre outil, de la position par défaut, de taille, de style d’ancrage et d’autres informations de visibilité est spécifié dans les valeurs facultatives. Pour plus d’informations sur l’inscription de fenêtre outil, consultez [Windows d’outil dans le Registre](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Informations d’affichage de fenêtre  
 Configuration de l’affichage de base d’une fenêtre outil est stockée dans jusqu'à six valeurs facultatives :  
  
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
  
|Name|Type|Données|Description|  
|----------|----------|----------|-----------------|  
|Name|REG_SZ|« Nom court s’affiche ici »|Un nom court qui décrit la fenêtre outil. Utilisé uniquement pour référence dans le Registre.|  
|Float|REG_SZ|« X1, Y1, X2, Y2 »|Quatre valeurs séparées par des virgules. X1, Y1 est la coordonnée de l’angle supérieur gauche de la fenêtre outil. X2, Y2 est la coordonnée de l’angle inférieur droit. Toutes les valeurs sont en coordonnées d’écran.|  
|Style|REG_SZ|« MDI »<br /><br /> « Flotter »<br /><br /> « Lié »<br /><br /> « Onglets »<br /><br /> « AlwaysFloat »|Un mot clé spécifiant initial afficher l’état de la fenêtre outil.<br /><br /> « MDI » = ancrée avec fenêtre MDI.<br /><br /> « Flotter » = flottante.<br /><br /> « Lié » = lié à une autre fenêtre (spécifiée dans l’entrée de fenêtre).<br /><br /> « Onglets » = combinées avec une autre fenêtre d’outil.<br /><br /> « AlwaysFloat » = ne peut pas être ancrée.<br /><br /> Pour plus d’informations, consultez la section commentaires ci-dessous.|  
|Fenêtre|REG_SZ|*\<GUID &GT;*|Le GUID d’une fenêtre à laquelle la fenêtre outil peut être liée ou avec onglets. Le GUID peut appartenir à un de vos propres windows ou l’une des fenêtres dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.|  
|Orientation|REG_SZ|« Left »<br /><br /> « Droite »<br /><br /> « Top »<br /><br /> « Bottom »|Consultez la section commentaires ci-dessous.|  
|DontForceCreate|REG_DWORD|0 ou 1|Lorsque cette entrée est présente et sa valeur n’est pas égal à zéro, la fenêtre est chargée, mais s’affiche pas immédiatement.|  
  
### <a name="comments"></a>Commentaires  
 L’entrée de l’Orientation définit la position où la fenêtre outil ancre lorsque l’utilisateur double-clique sur sa barre de titre. La position est relative à la fenêtre spécifiée dans l’entrée de la fenêtre. Si l’entrée de Style est définie sur « Lié », l’entrée de l’Orientation peut être « Left », « Droite », « Top » ou « Bottom ». Si l’entrée de Style est par « onglets », l’orientation de l’entrée peut être « gauche » ou « Right » et spécifie où l’onglet est ajouté. Si l’entrée de Style est « Flotter », la fenêtre Outil flotte tout d’abord. Lorsque vous double-cliquez sur la barre de titre, les entrées de l’Orientation et la fenêtre s’appliquent, et la fenêtre utilise le style par « onglets ». Si l’entrée de Style est « AlwaysFloat », la fenêtre outil ne peut pas être ancrée. Si l’entrée de Style est « MDI », la fenêtre outil est liée à la zone MDI, et l’entrée de la fenêtre est ignorée.  
  
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
 Valeurs dans la sous-clé de visibilité facultative déterminent les paramètres de visibilité d’une fenêtre outil. Les noms des valeurs sont utilisés pour stocker les GUID des commandes qui nécessitent une visibilité de la fenêtre. Si la commande est exécutée, l’IDE garantit que la fenêtre outil est créée et rendue visible.  
  
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
  
|Name|Type|Données|Description|  
|----------|----------|----------|-----------------|  
|(Default)|REG_SZ|Aucun.|Laissez vide.|  
|*\<GUID &GT;*|REG_DWORD ou REG_SZ|0 ou une chaîne descriptive.|Facultatif. Nom de l’entrée doit être le GUID d’une commande nécessitant une visibilité. La valeur conserve seulement une chaîne informative. En règle générale, la valeur est un `reg_dword` définie sur 0.|  
  
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

