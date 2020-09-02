---
title: Configuration de l’affichage de la fenêtre outil | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1af78bd58c42cf1312e36621011802e908c9e919
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186393"
---
# <a name="tool-window-display-configuration"></a>Configuration de l’affichage de la fenêtre Outil
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsqu’un VSPackage inscrit une fenêtre outil, la position, la taille, le style d’ancrage et d’autres informations de visibilité par défaut sont spécifiés dans les valeurs facultatives. Pour plus d’informations sur l’inscription de la fenêtre outil, consultez [fenêtres d’outils dans le registre](../extensibility/tool-windows-in-the-registry.md) .  
  
## <a name="window-display-information"></a>Informations d’affichage de la fenêtre  
 La configuration d’affichage de base d’une fenêtre outil est stockée dans six valeurs facultatives au maximum :  
  
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
|Nom|REG_SZ|« Nom abrégé ici »|Nom abrégé qui décrit la fenêtre outil. Utilisé uniquement pour la référence dans le registre.|  
|Float|REG_SZ|"X1, Y1, X2, Y2"|Quatre valeurs séparées par des virgules. X1, Y1 est la coordonnée de l’angle supérieur gauche de la fenêtre outil. X2, Y2 est la coordonnée du coin inférieur droit. Toutes les valeurs sont exprimées en coordonnées d’écran.|  
|Style|REG_SZ|FORMULAIRE<br /><br /> Dissocié<br /><br /> Liée<br /><br /> Defined<br /><br /> "AlwaysFloat"|Mot clé qui spécifie l’état d’affichage initial de la fenêtre outil.<br /><br /> « MDI » = ancré avec la fenêtre MDI.<br /><br /> « Float » = flottant.<br /><br /> « Linked » = lié à une autre fenêtre (spécifiée dans l’entrée de la fenêtre).<br /><br /> « Tabulé » = combiné avec une autre fenêtre outil.<br /><br /> « AlwaysFloat » = ne peut pas être ancré.<br /><br /> Pour plus d’informations, consultez la section commentaires ci-dessous.|  
|Fenêtre|REG_SZ|*\<GUID>*|GUID d’une fenêtre à laquelle la fenêtre outil peut être liée ou à onglets. Le GUID peut appartenir à l’une de vos fenêtres ou à l’une des fenêtres dans l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.|  
|Orientation|REG_SZ|Gauche<br /><br /> Approprié<br /><br /> Coin<br /><br /> Ballon|Consultez la section commentaires ci-dessous.|  
|DontForceCreate|REG_DWORD|0 ou 1|Lorsque cette entrée est présente et que sa valeur n’est pas égale à zéro, la fenêtre est chargée, mais pas immédiatement affichée.|  
  
### <a name="comments"></a>Commentaires  
 L’entrée d’orientation définit la position d’ancrage de la fenêtre outil lorsque l’utilisateur double-clique sur sa barre de titre. La position est relative à la fenêtre spécifiée dans l’entrée de la fenêtre. Si l’entrée de style est définie sur « liée », l’entrée d’orientation peut être « Left », « Right », « Top » ou « Bottom ». Si l’entrée de style est « tabulé », l’entrée d’orientation peut être « gauche » ou « droite » et spécifie l’emplacement où l’onglet est ajouté. Si l’entrée de style est « float », la fenêtre outil flotte en premier. Lorsque vous double-cliquez sur la barre de titre, les entrées d’orientation et de fenêtre s’appliquent et la fenêtre utilise le style « avec onglet ». Si l’entrée de style est « AlwaysFloat », la fenêtre outil ne peut pas être ancrée. Si l’entrée de style est « MDI », la fenêtre outil est liée à la zone MDI et l’entrée de la fenêtre est ignorée.  
  
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
 Les valeurs de la sous-clé de visibilité facultative déterminent les paramètres de visibilité d’une fenêtre outil. Les noms des valeurs sont utilisés pour stocker les GUID des commandes qui requièrent la visibilité de la fenêtre. Si la commande est exécutée, l’IDE garantit que la fenêtre outil est créée et rendue visible.  
  
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
|(Par défaut)|REG_SZ|None|Laissez vide.|  
|*\<GUID>*|REG_DWORD ou REG_SZ|0 ou une chaîne descriptive.|facultatif. Le nom de l’entrée doit être le GUID d’une commande nécessitant une visibilité. La valeur contient simplement une chaîne informatif. En règle générale, la valeur est `reg_dword` définie sur 0.|  
  
### <a name="example"></a> Exemple  
  
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
 [Essentiel des VSPackages](../misc/vspackage-essentials.md)
