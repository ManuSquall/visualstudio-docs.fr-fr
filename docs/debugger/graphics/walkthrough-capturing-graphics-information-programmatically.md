---
title: "Procédure pas à pas : Capture d’informations graphiques par programmation | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5adeff9-afaf-4047-b5ce-ef0aefe710eb
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2bf34eda9c9957b8a989244da3f2fce03a5d151e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Procédure pas à pas : capture d'informations Graphics par programmation
Vous pouvez utiliser les outils Graphics Diagnostics de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour capturer par programmation les informations graphiques d'une application Direct3D.  
  
 La capture par programmation est particulièrement utile dans les scénarios suivants :  
  
-   Commencez la capture par programmation quand votre application graphique n'utilise pas de chaîne de permutation, par exemple quand elle restitue une texture.  
  
-   Commencez la capture par programmation quand votre application n'effectue aucun rendu, par exemple, quand elle utilise DirectCompute pour les calculs.  
  
-   Appelez `CaptureCurrentFrame`quand un problème de rendu est difficile à prévoir et à capturer dans le cadre d'un test manuel, mais qui peut être prédit par programmation à partir d'informations sur l'état de l'application au moment de l'exécution.  
  
##  <a name="CaptureDX11_2"></a> Capture par programmation dans Windows 8.1  
 Cette partie de la procédure pas à pas illustre la capture par programmation dans des applications qui utilisent l'API DirectX 11.2 dans Windows 8.1, qui elle-même utilise la méthode de capture robuste. Pour plus d’informations sur l’utilisation de la capture par programmation dans les applications Windows 8 qui utilisent des versions antérieures de DirectX, consultez [Programmatic capture in Windows 8.0 and earlier](#CaptureDX11_1) , plus loin dans cette procédure pas à pas.  
  
 Cette section montre comment effectuer ces tâches :  
  
-   Préparation de votre application à l'utilisation de la capture par programmation  
  
-   Obtention de l'interface IDXGraphicsAnalysis  
  
-   Capture d'informations graphiques  
  
> [!NOTE]
>  Si les implémentations précédentes de la capture par programmation dépendaient des Outils de contrôle à distance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour fournir la fonctionnalité de capture, Windows 8.1 prend directement en charge la capture via Direct3D 11.2. Ainsi, vous n'avez plus besoin d'installer les Outils de contrôle à distance pour utiliser la capture par programmation dans Windows 8.1.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Préparation de votre application à l'utilisation de la capture par programmation  
 Pour utiliser la capture par programmation dans votre application, celle-ci doit inclure les en-têtes nécessaires. Ces en-têtes font partie du Kit de développement logiciel (SDK) Windows 8.1.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Pour inclure les en-têtes de capture par programmation  
  
-   Incluez les en-têtes suivants dans le fichier source où sera définie l'interface IDXGraphicsAnalysis :  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  N’incluez pas l’en-tête vsgcapture.h—which prend en charge par programmation capture de fichiers dans Windows 8.0 et versions antérieures, pour effectuer la capture par programmation dans vos applications Windows 8.1. Cet en-tête est incompatible avec DirectX 11.2. Si ce fichier est inclus après que l’en-tête d3d11_2.h est inclus, le compilateur émet un avertissement. Si vsgcapture.h est inclus avant d3d11_2.h, l’application ne démarrera pas.  
  
    > [!NOTE]
    >  Si le Kit de développement logiciel (SDK) DirectX de juin 2010 est installé sur votre machine et que le chemin include de votre projet contient `%DXSDK_DIR%includex86`, déplacez-le à la fin du chemin include. Faites-en autant pour le chemin d'accès à votre bibliothèque.  
  
#### <a name="windows-phone-81"></a>Windows Phone 8.1  
 Étant donné que le Kit de développement logiciel Windows Phone 8.1 n’inclut pas l’en-tête DXProgrammableCapture.h, vous devez définir le `IDXGraphicsAnalysis` interface vous-même afin que vous puissiez utiliser le `BeginCapture()` et `EndCapture()` méthodes. Incluez les autres en-têtes comme décrit dans la section précédente.  
  
###### <a name="to-define-the-idxgraphicsanalysis-interface"></a>Pour définir l'interface IDXGraphicsAnalysis  
  
-   Définissez l'interface IDXGraphicsAnalysis dans le fichier où vous avez inclus les fichiers d'en-tête.  
  
    ```  
    interface DECLSPEC_UUID("9f251514-9d4d-4902-9d60-18988ab7d4b5") DECLSPEC_NOVTABLE  
    IDXGraphicsAnalysis : public IUnknown  
    {  
        STDMETHOD_(void, BeginCapture)() PURE;  
        STDMETHOD_(void, EndCapture)() PURE;  
    };  
    ```  
  
 Pour des raisons pratiques, vous pouvez effectuer ces étapes dans un nouveau fichier d'en-tête et l'inclure là où votre application en a besoin.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>Obtention de l'interface IDXGraphicsAnalysis  
 Avant de pouvoir capturer les informations graphiques de DirectX 11.2, vous devez obtenir l'interface de débogage DXGI.  
  
> [!IMPORTANT]
>  Lorsque vous utilisez la capture par programmation, vous devez toujours exécuter votre application dans graphics diagnostics (Alt + F5 dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) ou sous la [outil de Capture de ligne de commande](command-line-capture-tool.md).  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Pour obtenir l'interface IDXGraphicsAnalysis  
  
-   Utilisez le code suivant pour raccorder l'interface IDXGraphicsAnalysis à l'interface de débogage DXGI.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     Veillez à examiner le `HRESULT` retourné par `DXGIGetDebugInterface1` pour vous assurer d'obtenir une interface valide avant de l'utiliser :  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    >  Si `DXGIGetDebugInterface1` renvoie `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), vérifiez que l’application est exécutée dans Graphics Diagnostics (Alt+F5 dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).  
  
### <a name="capturing-graphics-information"></a>Capture d'informations graphiques  
 Maintenant que vous avez une interface `IDXGraphicsAnalysis` valide, vous pouvez utiliser `BeginCapture` et `EndCapture` pour capturer des informations graphiques.  
  
##### <a name="to-capture-graphics-information"></a>Pour capturer des informations graphiques  
  
-   Pour commencer à capturer des informations graphiques, utilisez `BeginCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     La capture commence de suite après l'appel de `BeginCapture` ; il n'attend pas le frame suivant pour commencer. La capture s'arrête dès la présentation du frame actif ou l'appel de `EndCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
##  <a name="CaptureDX11_1"></a> Programmatic capture in Windows 8.0 and earlier  
 Cette partie de la procédure pas à pas illustre la capture par programmation dans des applications pour Windows 8.0 ou version antérieure qui utilisent l'API DirectX 11.1, qui elle-même utilise la méthode de capture héritée. Pour plus d’informations sur l’utilisation de la capture par programmation dans les applications Windows 8.1 qui utilisent DirectX 11.2, consultez [Capture par programmation dans Windows 8.1](#CaptureDX11_2) , plus haut dans cette procédure pas à pas.  
  
 Cette partie présente les tâches suivantes :  
  
-   Préparation de votre ordinateur à l'utilisation de la capture par programmation  
  
-   Préparation de votre application à l'utilisation de la capture par programmation  
  
-   Configuration du nom et de l'emplacement du fichier journal de graphisme  
  
-   Utilisation de l'API `CaptureCurrentFrame`  
  
### <a name="preparing-your-computer-to-use-programmatic-capture"></a>Préparation de votre ordinateur à l'utilisation de la capture par programmation  
 L'API de capture par programmation utilise les Outils de contrôle à distance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour proposer la fonctionnalité de capture. Les Outils de contrôle à distance doivent être installés sur l'ordinateur destiné à exécuter l'application, même quand vous utilisez la capture par programmation sur votre ordinateur local. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] n'a pas besoin de s'exécuter quand vous effectuez une capture par programmation sur un ordinateur local.  
  
 Pour utiliser les API de capture distante dans une application qui s'exécute sur un ordinateur, vous devez d'abord installer les Outils de contrôle à distance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sur cet ordinateur. Les plateformes matérielles prises en charge varient en fonction de la version des Outils de contrôle à distance. Pour plus d’informations sur l’installation des outils de contrôle à distance, consultez la [page de téléchargement des outils de contrôle à distance](http://go.microsoft.com/fwlink/p/?LinkId=246691) sur le site web des téléchargements Microsoft.  
  
 Sinon, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] installe les composants nécessaires pour assurer la capture distante pour les applications 32 bits.  
  
> [!NOTE]
>  Comme la plupart des applications de bureau Windows (y compris [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) ne sont pas prises en charge sous [!INCLUDE[win8](../includes/win8_md.md)] pour les appareils ARM, l'utilisation conjointe des Outils de contrôle à distance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et de l'API de capture par programmation est le seul moyen de capturer les diagnostics graphiques sur les appareils ARM.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Préparation de votre application à l'utilisation de la capture par programmation  
 Pour utiliser les outils Graphics Diagnostics, vous devez d'abord capturer les informations graphiques dont ils ont besoin. Vous pouvez capturer par programmation les informations à l'aide de l'API `CaptureCurrentFrame` .  
  
##### <a name="to-prepare-your-app-to-capture-graphics-information-programmatically"></a>Pour préparer votre application à la capture d'informations graphiques par programmation  
  
1.  Assurez-vous que l'en-tête `vsgcapture.h` est inclus dans le code source de l'application. Il peut être inclus à un seul emplacement (par exemple, dans le fichier de code source où vous prévoyez d'appeler l'API de capture par programmation) ou dans un fichier d'en-tête précompilé pour appeler l'API à partir de plusieurs fichiers de code source.  
  
2.  Dans le code source de l'application, chaque fois que vous voulez capturer le reste du frame actif, appelez `g_pVsgDbg->CaptureCurrentFrame()`. Cette méthode ne fait appel à aucun paramètre et ne retourne aucune valeur.  
  
### <a name="configuring-the-name-and-location-of-the-graphics-log-file"></a>Configuration du nom et de l'emplacement du fichier journal de graphisme  
 Le journal de graphisme est créé à l'emplacement défini par les macros `DONT_SAVE_VSGLOG_TO_TEMP` et `VSG_DEFAULT_RUN_FILENAME` .  
  
##### <a name="to-configure-the-name-and-location-of-the-graphics-log-file"></a>Pour configurer le nom et l'emplacement du fichier journal de graphisme  
  
-   Pour éviter que le journal de graphisme soit écrit dans le répertoire temporaire, avant la ligne `#include <vsgcapture.h>` , ajoutez ceci :  
  
    ```  
    #define DONT_SAVE_VSGLOG_TO_TEMP  
    ```  
  
     Vous pouvez définir cette valeur pour écrire le journal de graphisme à un emplacement relatif au répertoire de travail ou dans un chemin d'accès absolu si la définition de `VSG_DEFAULT_RUN_FILENAME` est un chemin d'accès absolu.  
  
-   Pour enregistrer le journal de graphisme à un emplacement différent ou pour lui donner un autre nom de fichier, avant la ligne `#include <vsgcapture.h>` , ajoutez ceci :  
  
    ```  
    #define VSG_DEFAULT_RUN_FILENAME <filename>  
    ```  
  
     Si vous n'effectuez pas cette étape, le nom de fichier est default.vsglog. Si vous n'avez pas défini `DONT_SAVE_VSGLOG_TO_TEMP`, l'emplacement du fichier est relatif au répertoire temporaire ; sinon, il est relatif au répertoire de travail ou se situe à un autre emplacement si vous avez spécifié un nom de fichier absolu.  
  
 Pour [!INCLUDE[win8_appname_long](../includes/win8_appname_long_md.md)] applications, l’emplacement du répertoire temporaire est propre à chaque utilisateur et l’application et se trouve généralement dans un emplacement tel que C:\users\\*nom d’utilisateur*\AppData\Local\Packages\\ *nom de famille de package*\TempState\\. Pour les applications de bureau, l’emplacement du répertoire temporaire est propre à chaque utilisateur et se trouve généralement dans un emplacement tel que C:\Users\\*nom d’utilisateur*\AppData\Local\Temp\\.  
  
> [!NOTE]
>  Pour écrire à un emplacement spécifique, vous devez avoir des autorisations d'accès en écriture à cet emplacement ; sinon, une erreur se produit. Gardez à l'esprit que les applications [!INCLUDE[win8_appname_long](../includes/win8_appname_long_md.md)] sont plus limitées que les applications de bureau en ce qui concerne l'écriture des données et qu'une configuration supplémentaire peut être nécessaire pour leur permettre d'écrire à certains emplacements.  
  
### <a name="capturing-the-graphics-information"></a>Capture des informations graphiques  
 Après avoir préparé l'application à la capture par programmation et éventuellement configuré l'emplacement et le nom du fichier journal de graphisme, générez, puis exécutez ou déboguez l'application pour capturer les données ; ne démarrez pas Graphics Diagnostics à partir de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] quand vous utilisez l'API de capture par programmation. Le journal de graphisme est écrit à l'emplacement que vous avez spécifié. Si vous voulez conserver cette version du journal, déplacez-le à un autre emplacement ; à défaut, il sera remplacé quand vous exécuterez à nouveau l'application.  
  
> [!TIP]
>  Vous pouvez toujours capturer les informations graphiques manuellement pendant que vous utilisez la capture par programmation : il vous suffit d'appuyer sur **Impr. écran**pendant que l'application a le focus. Vous pouvez employer cette technique pour capturer des informations graphiques supplémentaires qui ne sont pas capturées par l'API de capture par programmation.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette procédure pas à pas vous a montré comment capturer des informations graphiques par programmation. Pour franchir une étape supplémentaire, envisagez cette possibilité :  
  
-   Découvrez comment analyser les informations graphiques capturées à l'aide des outils Graphics Diagnostics. Consultez [vue d’ensemble](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Capture d’informations graphiques](walkthrough-capturing-graphics-information.md)   
 [Capture d’informations graphiques](capturing-graphics-information.md)   
 [Outil de capture en ligne de commande](command-line-capture-tool.md)