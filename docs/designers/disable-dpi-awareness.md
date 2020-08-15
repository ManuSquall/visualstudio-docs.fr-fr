---
title: Désactiver la prise en charge DPI dans Visual Studio
description: Décrit les limitations du Concepteur Windows Forms sur des moniteurs HDPI et explique comment exécuter Visual Studio comme processus sans prise en charge DPI.
ms.date: 04/05/2019
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.topic: conceptual
ms.openlocfilehash: 749a267d4fc33153cfc609f331ecd1d269706e12
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249964"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Désactiver la prise en charge DPI dans Visual Studio

Visual Studio est une application avec prise en charge DPI (points par pouce), ce qui signifie que l’affichage est mis à l’échelle automatiquement. Si une application est sans prise en charge DPI, le système d’exploitation met à l’échelle l’application en tant que bitmap. Ce comportement est également appelé « virtualisation DPI ». L’application pense qu’elle s’exécute toujours avec une mise à l’échelle de 100 %, soit 96 dpi.

Cet article décrit les limitations du Concepteur Windows Forms sur des moniteurs HDPI et explique comment exécuter Visual Studio comme processus sans prise en charge DPI.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Concepteur Windows Forms sur les moniteurs HDPI

Le **Concepteur Windows Forms** dans Visual Studio ne prend pas en charge la mise à l’échelle. Cela entraîne des problèmes d’affichage quand vous ouvrez des formulaires dans le **Concepteur Windows Forms** sur des moniteurs HDPI (nombre élevé de points par pouce). Par exemple, des contrôles peuvent sembler se chevaucher comme dans l’image suivante :

![Concepteur Windows Forms sur un moniteur HDPI](./media/win-forms-designer-hdpi.png)

Quand vous ouvrez un formulaire dans le **Concepteur Windows Forms** dans Visual Studio sur un moniteur HDPI, Visual Studio affiche une barre d’informations jaune en haut du concepteur :

![Barre d’informations dans Visual Studio pour redémarrer en mode sans prise en charge DPI](./media/scaling-gold-bar.png)

Le message lectures **de la mise à l’échelle sur votre écran principal est défini sur 200% (192 PPP). Cela peut entraîner des problèmes de rendu dans la fenêtre du concepteur.**

> [!NOTE]
> Cette barre d’informations a été introduite dans Visual Studio 2017 version 15.8.

Si vous ne travaillez pas dans le concepteur et que vous n’avez pas besoin d’ajuster la disposition de votre formulaire, vous pouvez ignorer la barre d’informations et continuer à travailler dans l’éditeur de code ou dans d’autres types de concepteurs. (Vous pouvez également [Désactiver les notifications](#disable-notifications) pour que la barre d’informations ne continue pas de s’afficher.) Seul le **Concepteur Windows Forms** est affecté. Si vous avez besoin de travailler dans le **Concepteur Windows Forms**, la section suivante vous aide à [résoudre le problème](#to-resolve-the-display-problem).

## <a name="to-resolve-the-display-problem"></a>Pour résoudre le problème d’affichage

Pour résoudre le problème d’affichage, vous avez trois options :

- [Redémarrer Visual Studio comme processus sans prise en charge DPI](#restart-visual-studio-as-a-dpi-unaware-process)
- [Ajouter une entrée de Registre](#add-a-registry-entry)
- [Définir le paramètre de mise à l’échelle de l’affichage avec la valeur 100 %](#set-your-display-scaling-setting-to-100)

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Redémarrer Visual Studio comme processus sans prise en charge DPI

Vous pouvez redémarrer Visual Studio comme processus sans prise en charge DPI en sélectionnant l’option dans la barre d’informations jaune. Il s’agit de la méthode recommandée pour résoudre le problème.

Quand Visual Studio s’exécute comme processus sans prise en charge DPI, les problèmes de disposition du concepteur sont résolus, mais les polices peuvent apparaître floues. Visual Studio affiche un message d’information jaune différent lorsqu’il s’exécute en tant que processus qui ne prend pas en charge la résolution PPP, indiquant que **Visual Studio s’exécute en tant que processus sans prise en charge dpi. Les concepteurs WPF et XAML peuvent ne pas s’afficher correctement.** La barre d’informations fournit également une option permettant de **redémarrer Visual Studio comme processus avec prise en charge DPI**.

> [!NOTE]
> - Si des fenêtres d’outil ne sont pas ancrées dans Visual Studio au moment de la sélection de l’option de redémarrage comme processus sans prise en charge DPI, la position de ces fenêtres peut changer.
> - Si vous utilisez le profil Visual Basic par défaut ou si l’option **Enregistrer les nouveaux projets lors de leur création** est désélectionnée dans **Outils** > **Options** > **Projets et solutions**, Visual Studio ne peut pas rouvrir votre projet quand il redémarre comme processus sans prise en charge DPI. Toutefois, vous pouvez ouvrir le projet en le sélectionnant sous **fichier**  >  **projets et solutions récents**.

Il est important de redémarrer Visual Studio comme processus avec prise en charge DPI quand vous avez fini de travailler dans le **Concepteur Windows Forms**. Quand il s’exécute comme processus sans prise en charge DPI, les polices peuvent paraître floues et vous pouvez constater des problèmes dans d’autres concepteurs, notamment dans le **Concepteur XAML**. Si vous fermez et rouvrez Visual Studio quand il s’exécute en mode sans prise en charge DPI, il repasse en mode avec prise en charge DPI. Vous pouvez également sélectionner l’option **redémarrer Visual Studio en tant que processus prenant en charge les PPP** dans la barre d’informations.

### <a name="add-a-registry-entry"></a>Ajouter une entrée de Registre

Vous pouvez marquer Visual Studio comme processus sans prise en charge DPI en modifiant le Registre. Ouvrez l’**Éditeur du Registre** et ajoutez une entrée à la sous-clé **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** :

**Entrée**: selon que vous utilisez Visual Studio 2017 ou 2019, utilisez l’une des valeurs suivantes :

- C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Si vous utilisez l’édition Professional ou Enterprise de Visual Studio, remplacez **Community** par **Professional** ou **Enterprise** dans l’entrée. Le cas échéant, remplacez également la lettre de lecteur.

**Type**: REG_SZ

**Valeur**: DPIUNAWARE

> [!NOTE]
> Visual Studio reste en mode sans prise en charge DPI jusqu’à ce que vous supprimiez l’entrée de Registre.

### <a name="set-your-display-scaling-setting-to-100"></a>Définir le paramètre de mise à l’échelle de l’affichage avec la valeur 100 %

Pour définir le paramètre de mise à l’échelle de l’affichage avec la valeur 100 % dans Windows 10, tapez **paramètres d’affichage** dans la zone de recherche de la barre des tâches, puis sélectionnez **Modifier les paramètres d’affichage**. Dans la fenêtre **Paramètres**, définissez **Modifier la taille du texte, des applications et d’autres éléments** avec la valeur **100 %**.

Le fait de définir la mise à l’échelle de l’affichage avec la valeur 100 % peut ne pas donner les résultats escomptés, car l’interface utilisateur risque d’être trop petite pour être utilisable.

## <a name="disable-notifications"></a>Désactiver les notifications

Vous pouvez choisir de ne pas être informé des problèmes de mise à l’échelle DPI dans Visual Studio. Vous pouvez par exemple désactiver les notifications si vous ne travaillez pas dans le concepteur.

Pour désactiver les notifications, choisissez **Outils**  >  **options** pour ouvrir la boîte de dialogue **options** . Ensuite, choisissez **Concepteur Windows Forms**  >  **général**et définissez les **notifications de mise à l’échelle dpi** sur **false**.

![Option Notifications de mise à l’échelle PPP dans Visual Studio](./media/notifications-option.png)

Pour réactiver par la suite les notifications de mise à l’échelle, affectez la valeur **True** à la propriété.

## <a name="troubleshoot"></a>Dépanner

Si le passage au mode avec prise en charge DPI ne fonctionne pas comme prévu dans Visual Studio, vérifiez si la valeur `dpiAwareness` est présente dans la sous-clé **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** de l’Éditeur du Registre. Si cette valeur est présente, supprimez-la.

## <a name="see-also"></a>Voir aussi

- [Mise à l’échelle automatique dans Windows Forms](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)
