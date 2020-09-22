---
title: Outil de capture en ligne de commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 208ff7f9bbfc2d07669a8b485edffc8dfc4cd54f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839790"
---
# <a name="command-line-capture-tool"></a>Outil en ligne de commande de capture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DXCap.exe est un outil en ligne de commande pour la capture et la lecture de Graphics Diagnostics. Il prend en charge tous les niveaux de fonctionnalités des versions Direct3D 10 à Direct3D 12.  
  
## <a name="syntax"></a>Syntaxe  
  
```ms-dos  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe –p [filename] –screenshot [-frame frames]  
DXCap.exe –p [filename] –toXML [xml_filename]  
DXCap.exe –v [–file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe –info  
```  
  
#### <a name="parameters"></a>Paramètres  
 `-file` `filename`  
 En mode de capture ( `-c` ), `filename` spécifie le nom du fichier journal de graphisme dans lequel les informations graphiques sont enregistrées. Si `filename` n’est pas spécifié, les informations graphiques sont enregistrées dans un fichier nommé `<appname>-<date>-<time>.vsglog` par défaut.  
  
 En mode de validation (v), `filename` spécifie le nom du fichier journal de graphisme à valider. Si `filename` n'est pas spécifié, le journal de graphisme validé en dernier est réutilisé.  
  
 `-frame` `frames`  
 En mode de capture, `frames` spécifie les frames que vous souhaitez capturer. Le premier frame est 1. Vous pouvez spécifier plusieurs frames à l'aide de virgules et de plages. Par exemple, si `frames` est `2, 5, 7-9, 15` , les frames,,,, `2` `5` `7` `8` `9` et `15` sont capturés.  
  
 `-period` `periods`  
 En mode de capture, `periods` spécifie les plages de temps, en secondes, pendant lesquelles vous souhaitez capturer des frames. Vous pouvez spécifier plusieurs périodes à l'aide de virgules et de plages. Par exemple `periods` , si est `2.1-5, 7.0-9.3` , les frames qui sont rendus entre `2.1` et `5` secondes, et entre `7` et `9.3` secondes sont capturés.  
  
 `-manual`  
 En mode de capture, `-manual` spécifie que les frames seront capturés manuellement en appuyant sur la touche Impr. écran. Les frames peuvent être capturés au démarrage de l'application. Pour arrêter la capture des frames, revenez à l'interface de ligne de commande et appuyez sur Entrée.  
  
 `-c` `app` [`args...`]  
 Mode de capture. En mode de capture, `app` spécifie le nom de l'application dont vous souhaitez capturer les informations graphiques. `args...` spécifie des paramètres de ligne de commande supplémentaires pour cette application.  
  
 `-p` [`filename`]  
 Mode de lecture ( `-p` ). En mode de lecture, `filename` spécifie le nom du fichier journal de graphisme à lire. Si `filename` n'est pas spécifié, le journal de graphisme lu en dernier est réutilisé.  
  
 `-debug`  
 En mode de lecture, `-debug` spécifie que la lecture doit être effectuée avec la couche de débogage Direct3D activée.  
  
 `-warp`  
 En mode de lecture, `-warp` spécifie que la lecture doit être effectuée à l’aide du convertisseur de logiciel Warp.  
  
 `-hw`  
 En mode de lecture, `-hw` spécifie que la lecture doit être effectuée à l’aide du matériel GPU.  
  
 `-config`  
 En mode de lecture, `-config` affiche des informations sur l’ordinateur qui a été utilisé pour capturer le fichier journal de graphisme, si ces informations ont été enregistrées dans le journal.  
  
 `-rawmode`  
 En mode de lecture, `-rawmode` spécifie que la lecture doit être effectuée sans modification des événements enregistrés. En situation normale, le mode de lecture peut apporter des changements mineurs à la lecture pour simplifier le débogage et accélérer cette dernière. Par exemple, il peut simuler la sortie de chaînes d'échange au lieu d'exécuter des commandes de chaînes d'échange. Généralement, ce n'est pas un problème. Toutefois, vous pouvez souhaiter que la lecture s'effectue de manière plus fidèle aux événements enregistrés. Par exemple, vous pouvez utiliser cette option pour restaurer le comportement de rendu en plein écran d'une application capturée durant son exécution en mode plein écran.  
  
 `-toXML` [`xml_filename`]  
 En mode de lecture, `xml_filename` spécifie le nom du fichier dans lequel une représentation XML de la lecture est écrite. Si `xml_filename` n’est pas spécifié, la représentation XML est écrite dans un fichier portant le même nom que le fichier en cours de lecture, mais avec l’extension `.xml`.  
  
 `-v`  
 Mode de validation. En mode de validation, les frames capturés sont lus par le matériel et par WARP. Leurs résultats sont comparés à l’aide d’une fonction de comparaison d’images. Vous pouvez utiliser cette fonctionnalité pour identifier rapidement les problèmes de pilote qui affectent le rendu.  
  
 `-examine` `events`  
 En mode de validation, `events` spécifie l'ensemble des événements graphiques dont les résultats immédiats sont comparés. Par exemple, `-examine present,draw,copy,clear` limite la comparaison uniquement aux événements appartenant à ces catégories.  
  
> [!TIP]
> Nous vous recommandons de commencer par `-examine present,draw,copy,clear` , car cela révèle la plupart des problèmes mais prend beaucoup moins de temps qu’un ensemble plus complet d’événements. Si nécessaire, vous pouvez spécifier un ensemble distinct ou plus important d'événements pour valider ces derniers et identifier d'autres genres de problèmes.  
  
 `-haltonfail`  
 En mode de validation, `-haltonfail` interrompt la validation quand des différences sont détectées entre le convertisseur matériel et Warp. La validation reprend dès que l’utilisateur appuie sur une touche.  
  
 `-exitonfail`  
 En mode de validation, `-exitonfail` quitte la validation immédiatement lorsque des différences sont détectées entre le convertisseur matériel et Warp. Quand le programme se termine de cette manière, il retourne `0` à l’environnement ; sinon, il retourne `1` .  
  
 `-showprogress`  
 En mode de validation, `-showprogress` affiche des informations sur la progression de la session de validation. La progression relative à WARP est affichée sur la gauche alors que la progression relative au matériel est affichée sur la droite.  
  
 `-e` `search_string`  
 Énumère les applications du Windows Store qui sont installées. Vous pouvez utiliser ces informations pour effectuer des captures des applications du Windows Store à l'aide de la ligne de commande.  
  
 `-info`  
 Affiche des informations sur les machines et capture les DLL.  
  
## <a name="remarks"></a>Remarques  
 DXCap.exe fonctionne en trois modes :  
  
 Mode de capture (-c)  
 Capture les informations graphiques d'une application en cours d'exécution et les enregistre dans un fichier journal de graphisme. Les fonctionnalités de capture et le format de fichier sont identiques à ceux de Visual Studio.  
  
 Mode de lecture (-p)  
 Lit les événements graphiques capturés d'un fichier journal de graphisme existant. Par défaut, la lecture s'effectue dans une fenêtre, même quand le fichier journal de graphisme a été capturé à partir d'une application en plein écran. La lecture s’effectue en mode plein écran uniquement lorsque le fichier journal de graphisme a été capturé à partir d’une application en plein écran et `–rawmode` est spécifié.  
  
 Mode de validation (`-v`)  
 Valide le comportement de rendu en lisant les frames capturés sur le matériel et dans WARP, puis compare leurs résultats à l'aide d'une fonction de comparaison d'images. Vous pouvez utiliser cette fonctionnalité pour identifier rapidement les problèmes de pilote qui affectent le rendu.  
  
 Outre ces modes, dxcap.exe exécute deux autres fonctions qui n'effectuent pas de capture ou de lecture des informations graphiques.  
  
 Fonction d’énumération ( `-e` )  
 Affiche des informations détaillées sur les applications du Windows Store installées sur la machine. Ces détails incluent le nom et l'appid de package qui identifient le fichier exécutable dans une application du Windows Store. Pour capturer les informations graphiques d'une application du Windows Store à l'aide de DXCap.exe, servez-vous du nom et de l'appid de package à la place du nom de fichier exécutable utilisé pour la capture d'une application de bureau.  
  
 Fonction info (`-info)`  
 Affiche des détails sur les machines et capture les DLL.  
  
## <a name="examples"></a>Exemples  
  
### <a name="capture-graphics-information-from-a-desktop-app"></a>Capturer les informations graphiques d'une application de bureau  
 Utilisez `–c` pour spécifier l’application à partir de laquelle vous souhaitez capturer les informations graphiques.  
  
```ms-dos  
DXCap.exe –c BasicHLSL11.exe  
```  
  
 Par défaut, les informations graphiques sont enregistrées dans un fichier nommé `<appname>-<date>-<time>.vsglog` . Utilisez `–file` pour spécifier un autre fichier à enregistrer.  
  
```ms-dos  
DXCap.exe –file regression_test_12.vsglog –c BasicHLSL11.exe  
```  
  
 Spécifiez des paramètres de ligne de commande supplémentaires pour l'application que vous capturez en les incluant après le nom de fichier de l'application.  
  
```ms-dos  
DXCap.exe –c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 La commande de l’exemple ci-dessus capture des informations graphiques de la version de bureau d’Internet Explorer tout en affichant la page web située à l’adresse www.fishgl.com, qui utilise l’API WebGL pour effectuer le rendu du contenu 3D.  
  
> [!NOTE]
> Dans la mesure où les arguments de ligne de commande qui apparaissent après l’application lui sont passés, vous devez spécifier les arguments destinés à DXCap.exe avant d’utiliser l’option `–c`.  
  
### <a name="capture-graphics-information-from-a-windows-store-app"></a>Capturer les informations graphiques d'une application du Windows Store  
 Vous pouvez capturer les informations graphiques d'une application du Windows Store.  
  
```ms-dos  
DXCap.exe –c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 La capture d'une application du Windows Store à l'aide de DXCap.exe ressemble à la capture d'une application de bureau Windows. Toutefois, au lieu d'identifier l'application de bureau par son nom de fichier, vous identifiez l'application du Windows Store par son nom de package, ainsi que par le nom ou l'ID de l'exécutable contenu dans le package à capturer. Pour faciliter la recherche des applications du Windows Store installées sur votre ordinateur, utilisez l' `–e` option avec DXCap.exe pour les énumérer :  
  
```ms-dos  
DXCap.exe -e  
```  
  
 Vous pouvez indiquer une chaîne de recherche facultative pour faciliter la recherche de l'application. Une fois que la chaîne de recherche a été fournie, DXCap.exe énumère les applications du Windows Store dont le nom de package, le nom d'application ou les ID d'application correspondent à la chaîne de recherche. La recherche respecte la casse.  
  
```ms-dos  
DXCap.exe –e map  
```  
  
 La commande ci-dessus énumère les applications du Windows Store qui correspondent à « map ». Voici la sortie :  
  
 **Package "Microsoft.BingMaps" :**  
 **InstallDirectory : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **FullName         : Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **UserSID          : S-1-5-21-2127521184-1604012920-1887927527-5603533**  
 **Name             : Microsoft.BingMaps**  
 **Publisher        : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US**  
 **Version          : 2.1.2914.1734**  
 **Applications accessibles :**  
 **Id   : AppexMaps**  
 **Exe  : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe**  
 **IsWWA: No**  
 **AppSpec (à lancer) : DXCap.exe-c Microsoft. BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe, AppexMaps** La dernière ligne de sortie pour chaque application énumérée affiche la commande que vous pouvez utiliser pour capturer des informations graphiques à partir de celle-ci.  
  
### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Capturer des frames spécifiques ou des frames situés à des périodes spécifiques  
 Utilisez `–frame` pour spécifier les frames que vous souhaitez capturer à l’aide de virgules et de plages :  
  
```ms-dos  
DXCap.exe –frame 2,5,7-9,15 –c SimpleBezier11.exe  
```  
  
 `–period`Vous pouvez utiliser pour spécifier un ensemble de périodes pendant lesquelles capturer des frames. Les intervalles de temps sont exprimés en secondes. Vous pouvez spécifier plusieurs plages :  
  
```ms-dos  
DXCap.exe –period 2.1-5, 7.0-9.3 –c SimpleBezier11.exe  
```  
  
### <a name="capture-frames-interactively"></a>Capturer des frames de manière interactive  
 Utilisez `–manual` pour capturer des frames de manière interactive. Appuyez sur la touche Entrée pour démarrer la capture, puis appuyez de nouveau sur Entrée pour l'arrêter.  
  
```ms-dos  
DXCap.exe –manual -c SimpleBezier11.exe  
```  
  
### <a name="play-back-a-graphics-log-file"></a>Lire un fichier journal de graphisme  
 Utilisez `-p` pour lire un fichier journal de graphisme capturé précédemment.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog  
```  
  
 Ignorez le nom de fichier pour lire le journal de graphisme capturé en dernier.  
  
```ms-dos  
DXCap.exe –p  
```  
  
### <a name="play-back-in-raw-mode"></a>Lire en mode brut  
 Utilisez `-rawmode` pour lire les commandes capturées exactement telles qu’elles se sont produites. En lecture normale, certaines commandes sont émulées. Par exemple, un fichier journal de graphisme capturé à partir d'une application en plein écran est lu dans une fenêtre. Quand le mode brut est activé, le même fichier est lu en plein écran dans la mesure du possible.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -rawmode  
```  
  
### <a name="play-back-using-warp-or-a-hardware-device"></a>Lire à l'aide de WARP ou d'un périphérique matériel  
 Vous pouvez forcer la lecture d'un fichier journal de graphisme capturé sur un périphérique matériel pour utiliser WARP. De même, vous pouvez forcer la lecture d'un journal capturé sur WARP pour utiliser un périphérique matériel. Utilisez `-warp` pour lire à l’aide de Warp.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -warp  
```  
  
 Utilisez `-hw` pour la lecture à l’aide du matériel.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -hw  
```  
  
### <a name="validate-a-graphics-log-file-against-warp"></a>Valider un fichier journal de graphisme par rapport à WARP  
 En mode de validation, le fichier journal de graphisme est lu sur le matériel et sur WARP, et leurs résultats sont comparés. Cela peut vous aider à identifier les erreurs de rendu provoquées par le pilote. Utilisez –v pour vérifier que le comportement du matériel graphique est correct par rapport à WARP.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 Pour réduire le nombre de comparaisons, vous pouvez spécifier une partie des commandes de validation à comparer. Les autres commandes seront ignorées. Utilisez –examine pour spécifier les commandes dont vous souhaitez comparer les résultats.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog –examine present,draw,copy,clear  
```  
  
### <a name="convert-a-graphics-log-file-to-pngs"></a>Convertir un fichier journal de graphisme en fichiers PNG  
 Pour afficher ou analyser les frames d'un fichier journal de graphisme, DXCap.exe peut enregistrer les frames capturés sous forme de fichiers image .png (Portable Network Graphics). Utilisez `-screenshot` to en mode de lecture pour sortir les frames capturés en tant que fichiers. png.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 Utilisez `–frame` avec `–screenshot` pour spécifier les frames que vous souhaitez générer.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot –frame 5, 7-9  
```  
  
### <a name="convert-a-graphics-log-file-to-xml"></a>Convertir un fichier journal de graphisme au format XML  
 Pour permettre le traitement et l'analyse des journaux de graphisme à l'aide d'outils familiers tels que FindStr ou XSLT, DXCap.exe peut convertir un fichier journal de graphisme au format XML. Utilisez `-toXML` le mode de lecture pour convertir le journal au format XML au lieu de le relire.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML  
```  
  
 Par défaut, la sortie XML est écrite dans un fichier qui porte le même nom que le journal de graphisme, mais dont l'extension est .xml. Dans l’exemple ci-dessus, le fichier XML est nommé **regression_test_12.xml**. Pour attribuer au fichier XML un nom différent, spécifiez-le après `-toXML` .  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML temp.xml  
```  
  
 Le fichier résultant contient du code XML qui ressemble à ce qui suit :  
  
```xml  
<Moment value="67"/>  
<Method name="CreateDXGIFactory1" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />  
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />  
</Method>  
  
<Moment value="167"/>  
<Method name="D3D11CreateDevice" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />  
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />  
    <Parameter name="Software" type="HMODULE" value="pointer" />  
    <Parameter name="Flags" type="UINT" value="0" />  
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >  
        <Element value="D3D_FEATURE_LEVEL_11_0" />  
    </Parameter>  
    <Parameter name="FeatureLevels" type="UINT" value="1" />  
    <Parameter name="SDKVersion" type="UINT" value="7" />  
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />  
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />  
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />  
</Method>  
```  
  
## <a name="requirements"></a>Spécifications
