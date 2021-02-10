---
title: Utilisation de contrôles HTML5 dans des tests codés de l'interface utilisateur
description: En savoir plus sur la prise en charge des tests codés de l’interface utilisateur pour les contrôles HTML5 inclus dans Internet Explorer 9 et Internet Explorer 10.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 931db4db8b6dd5b076ab720c866bb2b5b97aa15c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946356"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Utilisation de contrôles HTML5 dans des tests codés de l’interface utilisateur

Les tests codés de l'interface utilisateur incluent la prise en charge d'une partie des contrôles HTML5 inclus dans Internet Explorer 9 et Internet Explorer 10.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Configuration requise**

- Visual Studio Enterprise

> [!WARNING]
> Dans les versions antérieures à Internet Explorer 10, il était possible d'exécuter des tests codés de l'interface utilisateur à un niveau de privilège plus élevé que celui du processus Internet Explorer. Quand vous exécutez des tests codés de l'interface utilisateur dans Internet Explorer 10, le test codé de l'interface utilisateur et le processus Internet Explorer doivent être au même niveau de privilège. Cette obligation est due aux fonctionnalités AppContainer plus sécurisées dans Internet Explorer 10.

> [!WARNING]
> Si vous créez un test codé de l'interface utilisateur dans Internet Explorer 10, il risque de ne pas s'exécuter avec Internet Explorer 9 ou Internet Explorer 8. Cela tient au fait qu'Internet Explorer 10 inclut des contrôles HTML5 tels que des contrôles Audio, Video, ProgressBar et Slider. Ces contrôles HTML5 ne sont pas reconnus par Internet Explorer 9 ni Internet Explorer 8. De même, votre test codé de l’interface utilisateur avec Internet Explorer 9 peut inclure certains contrôles HTML5 qui ne seront pas non plus reconnus dans Internet Explorer 8.

## <a name="audio-control"></a>Contrôle Audio

**Contrôle Audio :** les actions sur le contrôle Audio HTML5 sont correctement enregistrées et lues.

![Contrôle audio HTML5](../test/media/codedui_html5_audio.png)

|Action|Enregistrement|Code généré|
|-|---------------|-|
|**Lire l’audio**<br /><br /> Directement à partir du contrôle ou dans le menu contextuel (clic droit) du contrôle.|Lire l' \<name> audio de 00:00:00|HtmlAudio.Play(TimeSpan)|
|**Rechercher un moment précis dans le fichier audio**|Rechercher \<name> du son sur 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**Suspendre la lecture du fichier audio**<br /><br /> Directement à partir du contrôle ou dans le menu contextuel (clic droit) du contrôle.|Suspendre l' \<name> audio à 00:01:53|HtmlAudio.Pause(TimeSpan)|
|**Désactiver le son**<br /><br /> Directement à partir du contrôle ou dans le menu contextuel (clic droit) du contrôle.|Désactiver le \<name> son|HtmlAudio.Mute()|
|**Réactiver le son**<br /><br /> Directement à partir du contrôle ou dans le menu contextuel (clic droit) du contrôle.|Activer le \<name> son|HtmlAudio.Unmute()|
|**Modifier le volume audio**|Définir le volume de l' \<name> audio sur 79%|HtmlAudio.SetVolume(float)|

Consultez [HTMLAudioElement](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement) pour obtenir une liste de propriétés sur lesquelles vous pouvez ajouter une assertion.

**Propriétés de recherche :** Les propriétés de recherche pour `HtmlAudio` sont `Id` , `Name` et `Title` .

**Propriétés du filtre :** Les propriétés de filtre `HtmlAudio` pour `Src` sont `Class` , `ControlDefinition` et `TagInstance` .

> [!NOTE]
> La durée de Seek et Pause peut être considérable. Lors de la lecture, le test codé de l'interface utilisateur attend que la durée spécifiée dans `(TimeSpan)` soit écoulée avant de suspendre l'audio. Si dans certaines circonstances particulières, la durée spécifiée s'est écoulée avant l'activation de la commande Pause, une exception est levée.

## <a name="video-control"></a>Contrôle Video
**Contrôle Video :** les actions sur le contrôle Video HTML5 sont correctement enregistrées et lues.

![Contrôle vidéo HTML5](../test/media/codedui_html5_video.png)

|Action|Enregistrement|Code généré|
|-|---------------|-|
|**Lecture vidéo**<br /><br /> Directement à partir du contrôle ou dans le menu contextuel (clic droit) du contrôle.|Lire la \<name> vidéo à partir de 00:00:00|HtmlVideo.Play(TimeSpan)|
|**Rechercher un moment précis dans le fichier vidéo**|Recherche \<name> de vidéos sur 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Suspendre la lecture du fichier vidéo**<br /><br /> Directement à partir du contrôle ou dans le menu contextuel (clic droit) du contrôle.|Suspendre la \<name> vidéo à 00:01:53|HtmlVideo.Pause(TimeSpan)|
|**Désactiver le son de la vidéo**<br /><br /> Directement à partir du contrôle ou dans le menu contextuel (clic droit) du contrôle.|\<name>Vidéo muet|HtmlVideo.Mute()|
|**Réactiver le son de la vidéo**<br /><br /> Directement à partir du contrôle ou dans le menu contextuel (clic droit) du contrôle.|Vidéo muette \<name>|HtmlVideo.Unmute()|
|**Modifier le volume de la vidéo**|Définir le volume de la \<name> vidéo sur 79%||

Consultez [HTMLVideoElement](https://developer.mozilla.org/docs/Web/HTML/Element/video) pour obtenir une liste de propriétés sur lesquelles vous pouvez ajouter une assertion.

**Propriétés de recherche :** Les propriétés de recherche pour `HtmlVideo` sont `Id` , `Name` et `Title` .

**Propriétés du filtre :** Les propriétés de filtre `HtmlVideo` pour `Src` sont `Poster` , `Class` , `ControlDefinition` et `TagInstance` .

> [!NOTE]
> Si vous rembobinez ou avancez rapidement la vidéo à l'aide d'étiquettes-30s ou +30s, celle-ci est agrégée pour rechercher le moment précis.

## <a name="progressbar"></a>Barre de progression
**Contrôle ProgressBar :** ProgressBar est un contrôle sur lequel il n’est pas possible d’interagir. Vous pouvez ajouter des assertions sur les propriétés `Value` et `Max` de ce contrôle. Pour plus d’informations, consultez [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

![Contrôle de barre de progression HTML5](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Voir aussi

- [Éléments HTML](https://developer.mozilla.org/docs/Web/HTML/Element)
- [Utiliser UI Automation pour tester votre code](../test/use-ui-automation-to-test-your-code.md)
- [Créer des tests codés de l’interface utilisateur](../test/use-ui-automation-to-test-your-code.md)
- [Configurations et plateformes prises en charge pour les tests codés de l’interface utilisateur et les enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
