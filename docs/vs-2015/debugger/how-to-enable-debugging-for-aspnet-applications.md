---
title: 'Procédure : Activer le débogage pour les Applications ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 07036fd7c1db7dc8b56502ab9c914f1ba808e876
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703664"
---
# <a name="how-to-enable-debugging-for-aspnet-applications"></a>Procédure : Activer le débogage pour les Applications ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour activer le débogage, vous devez l’activer à la fois dans la page **Propriétés du projet** et dans le fichier web.config de l’application.  
  
> [!NOTE]  
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Paramètres Visual Studio](https://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>Pour activer le débogage ASP.NET dans les propriétés de projet (Visual Basic/C#)  
  
1. Dans l’ **Explorateur de solutions**, cliquez avec le bouton droit sur le nom d’un projet web, puis sélectionnez **Propriétés**.  
  
2. Dans la page de propriétés du projet, cliquez sur l’onglet **Web** .  
  
3. Sous **Débogueurs**, cochez la case **ASP.NET** .  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>Pour activer le débogage dans un fichier web.config  
  
1. Ouvrez le fichier web.config dans l’éditeur de texte standard ou l’analyseur XML de votre choix.  
  
    > [!NOTE]  
    > Vous ne pouvez pas accéder au fichier à distance si vous utilisez un navigateur web. Pour des raisons de sécurité, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] configure Microsoft IIS pour empêcher le navigateur d’accéder directement aux fichiers web.config. Si vous essayez d’accéder à un fichier de configuration à l’aide d’un navigateur, vous obtenez une erreur 403 d’accès HTTP (interdit).  
  
2. Le fichier web.config est un fichier XML qui contient des sections imbriquées marquées par des balises. Recherchez l’élément `configuration/system.web/compilation` . Si l’élément de compilation n’existe pas, créez-le.  
  
3. Si l’élément `compilation` ne contient pas d’attribut `debug` , ajoutez cet attribut à l’élément.  
  
4. Assurez-vous que l’attribut `debug` est défini sur `true`.  
  
Le fichier web.config doit ressembler à l’exemple suivant. Notez qu’il peut y avoir des sections entre les éléments de configuration et les éléments system.web :  
  
- sections d’éléments entre les éléments de configuration et les éléments system.web  
  
- sections d’éléments entre les éléments system.web et les éléments de compilation  
  
- L’élément de compilation peut contenir d’autres éléments et attributs  
  
## <a name="example"></a>Exemple  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```  
  
## <a name="robust-programming"></a>Programmation fiable  
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] détecte automatiquement les modifications apportées aux fichiers web.config et applique les nouveaux paramètres de configuration. Vous n’avez pas à redémarrer l’ordinateur ni à redémarrer le serveur IIS pour que les modifications prennent effet.  
  
Un site web peut contenir plusieurs répertoires et sous-répertoires virtuels, et chacun d’eux peut contenir des fichiers web.config. Les applications [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] héritent des paramètres des fichiers web.config à des niveaux supérieurs dans le chemin d’URL. Les fichiers de configuration hiérarchiques permettent de modifier les paramètres de plusieurs applications [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] en même temps, par exemple, les paramètres de toutes les applications situées à un niveau inférieur dans la hiérarchie. Toutefois, si `debug` est défini dans un fichier situé à un niveau hiérarchique inférieur, il remplace la valeur la plus élevée.  
  
Par exemple, vous pouvez spécifier `debug="true"` dans www.microsoft.com/aaa/Web.config. Ainsi, les applications contenues dans le dossier aaa ou dans ses sous-dossiers hériteront de ce paramètre. Par conséquent, si votre [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] application se trouve dans www.microsoft.com/aaa/bbb, elle héritera de ce paramètre, tout comme les [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] applications dans www.microsoft.com/aaa/ccc, www.microsoft.com/aaa/ddd et ainsi de suite. La seule exception concerne le cas où l’une de ces applications remplace le paramètre à l’aide de son propre fichier Web.config de niveau inférieur.  
  
L’activation du mode débogage affecte considérablement les performances de votre application [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Pensez à désactiver le mode débogage avant de déployer une application release ou de mesurer les performances.  
  
## <a name="see-also"></a>Voir aussi  
[Débogage d’applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)  
