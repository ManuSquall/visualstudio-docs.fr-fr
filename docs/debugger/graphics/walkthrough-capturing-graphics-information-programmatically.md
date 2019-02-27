---
title: 'Procédure pas à pas : Capture d’informations graphiques par programmation | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fa8d750049d7d74d912e68544c91d5006252068
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722913"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Procédure pas à pas : capture d'informations Graphics par programmation
Vous pouvez utiliser les outils Graphics Diagnostics de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour capturer par programmation les informations graphiques d'une application Direct3D.

La capture par programmation est particulièrement utile dans les scénarios suivants :

- Commencez la capture par programmation quand votre application graphique n'utilise pas de chaîne de permutation, par exemple quand elle restitue une texture.

- Commencez la capture par programmation quand votre application n'effectue aucun rendu, par exemple, quand elle utilise DirectCompute pour les calculs.

- Appelez `CaptureCurrentFrame`quand un problème de rendu est difficile à prévoir et à capturer dans le cadre d'un test manuel, mais qui peut être prédit par programmation à partir d'informations sur l'état de l'application au moment de l'exécution.

## <a name="CaptureDX11_2"></a> Capture par programmation dans Windows 10
Cette partie de la procédure pas à pas illustre la capture par programmation dans des applications qui utilisent l’API DirectX 11.2 dans Windows 10, qui elle-même utilise la méthode de capture robuste.

Cette section montre comment effectuer ces tâches :

- Préparation de votre application à l'utilisation de la capture par programmation

- Obtention de l'interface IDXGraphicsAnalysis

- Capture d'informations graphiques

> [!NOTE]
> Les implémentations précédentes de capture par programmation dépendaient des outils à distance pour Visual Studio pour [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour fournir des fonctionnalités de capture.

### <a name="preparing-your-app-to-use-programmatic-capture"></a>Préparation de votre application à l'utilisation de la capture par programmation
Pour utiliser la capture par programmation dans votre application, celle-ci doit inclure les en-têtes nécessaires. Ces en-têtes font partie du Kit SDK Windows 10.

##### <a name="to-include-programmatic-capture-headers"></a>Pour inclure les en-têtes de capture par programmation

- Incluez les en-têtes suivants dans le fichier source où sera définie l'interface IDXGraphicsAnalysis :

    ```cpp
    #include <DXGItype.h>
    #include <dxgi1_2.h>
    #include <dxgi1_3.h>
    #include <DXProgrammableCapture.h>
    ```

    > [!IMPORTANT]
    > N’incluez pas le fichier d’en-tête vsgcapture.h (qui prend en charge la capture par programmation dans Windows 8.0 et versions antérieures) pour utiliser la capture par programmation dans vos applications Windows 10. Cet en-tête est incompatible avec DirectX 11.2. Si ce fichier est inclus après que l’en-tête d3d11_2.h est inclus, le compilateur émet un avertissement. Si vsgcapture.h est inclus avant d3d11_2.h, l’application ne démarre pas.

    > [!NOTE]
    > Si le Kit de développement logiciel (SDK) DirectX de juin 2010 est installé sur votre machine et que le chemin include de votre projet contient `%DXSDK_DIR%includex86`, déplacez-le à la fin du chemin include. Faites-en autant pour le chemin d'accès à votre bibliothèque.

### <a name="getting-the-idxgraphicsanalysis-interface"></a>Obtention de l'interface IDXGraphicsAnalysis
Avant de pouvoir capturer les informations graphiques de DirectX 11.2, vous devez obtenir l'interface de débogage DXGI.

> [!IMPORTANT]
> Lorsque vous utilisez la capture par programmation, vous devez toujours exécuter votre application dans graphics diagnostics (Alt + F5 dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) ou sous la [l’outil de ligne de commande de Capture](command-line-capture-tool.md).

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Pour obtenir l'interface IDXGraphicsAnalysis

- Utilisez le code suivant pour raccorder l'interface IDXGraphicsAnalysis à l'interface de débogage DXGI.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  Veillez à consulter le `HRESULT` retourné par [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) pour vous assurer d’obtenir une interface valide avant de l’utiliser :

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > Si `DXGIGetDebugInterface1` renvoie `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), vérifiez que l’application est exécutée dans Graphics Diagnostics (Alt+F5 dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).

### <a name="capturing-graphics-information"></a>Capture d'informations graphiques
Maintenant que vous avez une interface `IDXGraphicsAnalysis` valide, vous pouvez utiliser `BeginCapture` et `EndCapture` pour capturer des informations graphiques.

##### <a name="to-capture-graphics-information"></a>Pour capturer des informations graphiques

- Pour commencer à capturer des informations graphiques, utilisez `BeginCapture`:

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    La capture commence de suite après l'appel de `BeginCapture` ; il n'attend pas le frame suivant pour commencer. La capture s'arrête dès la présentation du frame actif ou l'appel de `EndCapture`:

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- Après l’appel à `EndCapture`, libérer l’objet graphics.

## <a name="next-steps"></a>Étapes suivantes
Cette procédure pas à pas vous a montré comment capturer des informations graphiques par programmation. Pour franchir une étape supplémentaire, envisagez cette possibilité :

- Découvrez comment analyser les informations graphiques capturées à l'aide des outils Graphics Diagnostics. Consultez [vue d’ensemble](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : capture d’informations graphiques](walkthrough-capturing-graphics-information.md)
- [Capturing Graphics Information](capturing-graphics-information.md)
- [Outil de capture en ligne de commande](command-line-capture-tool.md)
