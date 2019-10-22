---
title: Utilisation de contrôles HTML5 dans des tests codés de l’interface utilisateur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: 19
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 029b547102863f4798ad261deb678c4d98596916
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657202"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Utilisation de contrôles HTML5 dans des tests codés de l'interface utilisateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les tests codés de l'interface utilisateur incluent la prise en charge d'une partie des contrôles HTML5 inclus dans Internet Explorer 9 et Internet Explorer 10.

 **Prérequis**

- Visual Studio Enterprise

> [!WARNING]
> Dans les versions antérieures à Internet Explorer 10, il était possible d'exécuter des tests codés de l'interface utilisateur à un niveau de privilège plus élevé que celui du processus Internet Explorer. Quand vous exécutez des tests codés de l'interface utilisateur dans Internet Explorer 10, le test codé de l'interface utilisateur et le processus Internet Explorer doivent être au même niveau de privilège. Cette obligation est due aux fonctionnalités AppContainer plus sécurisées dans Internet Explorer 10.

> [!WARNING]
> Si vous créez un test codé de l'interface utilisateur dans Internet Explorer 10, il risque de ne pas s'exécuter avec Internet Explorer 9 ou Internet Explorer 8. Cela tient au fait qu'Internet Explorer 10 inclut des contrôles HTML5 tels que des contrôles Audio, Video, ProgressBar et Slider. Ces contrôles HTML5 ne sont pas reconnus par Internet Explorer 9 ni Internet Explorer 8. De même, votre test codé de l’interface utilisateur avec Internet Explorer 9 peut inclure certains contrôles HTML5 qui ne seront pas non plus reconnus dans Internet Explorer 8.

## <a name="supported-html5-controls"></a>Contrôles HTML5 pris en charge
 Les tests codés de l’interface utilisateur prennent en charge l’enregistrement, la lecture et la validation des contrôles HTML5 suivants :

- [Contrôle Audio](#audio-control)

- [Contrôle Video](#video-control)

- [Slider](#slider)

- [ProgressBar](#progressbar)

### <a name="audio-control"></a>Contrôle Audio
 **Contrôle Audio :** les actions sur le contrôle Audio HTML5 sont correctement enregistrées et lues.

 ![Contrôle audio HTML5](../test/media/codedui-html5-audio.png)

|Action|Enregistrement|Code généré|
|------------|---------------|--------------------|
|**Lire un fichier audio**<br /><br /> Directement à partir du contrôle ou à partir du menu contextuel des contrôles.|Play \<nom> Audio from 00:00:00|HtmlAudio.Play(TimeSpan)|
|**Rechercher un moment précis dans le fichier audio**|Seek \<nom> Audio to 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**Suspendre la lecture du fichier audio**<br /><br /> Directement à partir du contrôle ou à partir du menu contextuel des contrôles.|Pause \<nom> Audio at 00:01:53|HtmlAudio.Pause(TimeSpan)|
|**Désactiver le son**<br /><br /> Directement à partir du contrôle ou à partir du menu contextuel des contrôles.|Mute \<nom> Audio|HtmlAudio.Mute()|
|**Réactiver le son**<br /><br /> Directement à partir du contrôle ou à partir du menu contextuel des contrôles.|Unmute \<nom> Audio|HtmlAudio.Unmute()|
|**Modifier le volume audio**|Set volume of \<nom> Audio to 79%|HtmlAudio.SetVolume(float)|

 Les propriétés suivantes sont disponibles pour HtmlAudio et vous pouvez ajouter une assertion sur chacune d'entre elles :

```
string AutoPlay
string Controls
string CurrentSrc
string CurrentTime
string CurrentTimeAsString
string Duration
string DurationAsString
string Ended
string Loop
string Muted
string Paused
string PlaybackRate
string ReadyState
string Seeking
string Src
string Volume
```

 **Propriétés de recherche** : les propriétés de recherche pour `HtmlAudio` sont `Id`, `Name` et `Title`.

 **Propriétés de filtre :** les propriétés de filtre pour `HtmlAudio` sont `Src`, `Class`, `ControlDefinition` et `TagInstance`.

> [!NOTE]
> La durée de Seek et Pause peut être considérable. Lors de la lecture, le test codé de l'interface utilisateur attend que la durée spécifiée dans `(TimeSpan)` soit écoulée avant de suspendre l'audio. Si dans certaines circonstances particulières, la durée spécifiée s'est écoulée avant l'activation de la commande Pause, une exception est levée.

### <a name="video-control"></a>Contrôle Video
 **Contrôle Video :** les actions sur le contrôle Video HTML5 sont correctement enregistrées et lues.

 ![Contrôle vidéo HTML5](../test/media/codedui-html5-video.png)

|Action|Enregistrement|Code généré|
|------------|---------------|--------------------|
|**Lire un fichier vidéo**<br /><br /> Directement à partir du contrôle ou à partir du menu contextuel des contrôles.|Play \<nom> Video from 00:00:00|HtmlVideo.Play(TimeSpan)|
|**Rechercher un moment précis dans le fichier vidéo**|Seek \<nom> Video to 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Suspendre la lecture du fichier vidéo**<br /><br /> Directement à partir du contrôle ou à partir du menu contextuel des contrôles.|Pause \<nom> Video at 00:01:53|HtmlVideo.Pause(TimeSpan)|
|**Désactiver le son de la vidéo**<br /><br /> Directement à partir du contrôle ou à partir du menu contextuel des contrôles.|Mute \<nom> Video|HtmlVideo.Mute()|
|**Réactiver le son de la vidéo**<br /><br /> Directement à partir du contrôle ou à partir du menu contextuel des contrôles.|Unmute \<nom> Video|HtmlVideo.Unmute()|
|**Modifier le volume de la vidéo**|Set volume of \<nom> Video to 79%||

 Toutes les propriétés de HtmlAudio sont disponibles pour HtmlVideo. En outre, les trois propriétés suivantes sont également disponibles. Il est possible d'ajouter une assertion sur chacune d'entre elles.

```
string Poster
string VideoHeight
string VideoWidth

```

 **Propriétés de recherche** : les propriétés de recherche pour `HtmlVideo` sont `Id`, `Name` et `Title`.

 **Propriétés de filtre :** les propriétés de filtre pour `HtmlVideo` sont `Src`, `Poster`, `Class`, `ControlDefinition` et `TagInstance`.

> [!NOTE]
> Si vous rembobinez ou avancez rapidement la vidéo à l'aide d'étiquettes-30s ou +30s, celle-ci est agrégée pour rechercher le moment précis.

### <a name="slider"></a>Curseur
 **Contrôle Slider :** les actions sur le contrôle Slider HTML5 sont correctement enregistrées et lues.

 ![Commande de réglage HTML5](../test/media/codedui-html5-slider.png)

|Action|Enregistrement|Code généré|
|------------|---------------|--------------------|
|**Définir une position dans le contrôle Slider**|Set position to \<x> in \<nom> slider|HtmlSlider.ValueAsNumber=\<x>|

 Les propriétés suivantes sont disponibles pour HtmlSlider et il est possible d'ajouter une assertion sur chacune d'entre elles :

```
string Disabled
string Max
string Min
string Required
string Step
string ValueAsNumber
```

### <a name="progressbar"></a>Barre de progression
 **Contrôle ProgressBar :** ProgressBar est un contrôle sur lequel il n’est pas possible d’interagir. Vous pouvez ajouter des assertions sur les propriétés `Value` et `Max` de ce contrôle.

 ![Contrôle de barre de progression HTML5](../test/media/codedui-html5-progressbar.png)

## <a name="see-also"></a>Voir aussi

- [Éléments HTML](https://www.w3schools.com/HTML/html_elements.asp)
- [Utiliser l’automatisation de l’interface utilisateur pour tester votre code](../test/use-ui-automation-to-test-your-code.md)
- [Création de tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Personnalisation de votre test codé de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)
- [Plateformes et configurations prises en charge pour les tests codés de l’interface utilisateur et les enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
