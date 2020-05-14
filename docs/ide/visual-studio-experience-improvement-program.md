---
title: Programme d'amélioration du produit
description: Découvrez comment gérer les paramètres de confidentialité dans Visual Studio.
ms.date: 05/21/2018
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6c785b755b64f0dd7e367a01d9c05c1981ea558
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71693011"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Programme d’amélioration du produit Visual Studio

Le programme VSCEIP (Programme d’amélioration du produit Visual Studio) est conçu pour aider Microsoft à améliorer Visual Studio au fil du temps. Ce programme [collecte des informations sur les erreurs](../ide/diagnostic-data-collection.md), le matériel informatique et la façon dont les utilisateurs se servent de Visual Studio, sans les interrompre dans leurs tâches. Les informations collectées permettent à Microsoft d’identifier les fonctionnalités à améliorer. Ce document explique comment accepter ou refuser de participer au programme VSCEIP.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> La télémétrie VSCEIP opte dans ou hors des paramètres ne s’appliquent pas à 'Report a Problem' dans Visual Studio. Lorsque vous signalez qu’un problème, les journaux sont collectés et envoyés à Microsoft uniquement lorsque vous fournissez la permission en cliquant sur 'Submit'. Si vous êtes intéressé à gérer les journaux avant de vous soumettre à «Signaler un problème», veuillez consulter [la confidentialité des données de rétroaction](./developer-community-privacy.md) pour plus de détails.

## <a name="opt-in-or-out"></a>Accepter ou refuser de participer

Le programme VSCEIP est activé par défaut. Vous pouvez le désactiver ou le réactiver en suivant les instructions ci-après :

1. Dans Visual Studio, choisissez **Help** > **Send Feedback,** puis sélectionnez **Paramètres**.

   La boîte de dialogue **Programme d’amélioration de l’expérience utilisateur Visual Studio** s’ouvre.

1. Pour refuser de participer, sélectionnez **Non, je ne souhaite pas participer**, puis sélectionnez **OK**. Pour accepter de participer, sélectionnez **Oui, je souhaite participer**, puis sélectionnez **OK**.

   ![Boîte de dialogue Programme d’amélioration de l’expérience utilisateur Visual Studio](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Paramètres du Registre

Si vous installez [Visual Studio Build Tools](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017), vous devez mettre à jour le Registre pour configurer le programme VSCEIP. Les clients en entreprise peuvent créer une stratégie de groupe pour accepter ou refuser le programme VSCEIP en définissant une stratégie basée sur le Registre.

La clé de Registre et les paramètres pertinents se présentent comme suit :

::: moniker range="vs-2017"

- Sur un OS 64 bits, clé = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- Sur un OS 32 bits, clé = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Lorsque la politique de groupe est activée, La clé **HKEY_LOCAL_MACHINE-Software-Policies-Microsoft-VisualStudio-SQM**

::: moniker-end

::: moniker range=">=vs-2019"

- Sur un système d’exploitation 64 bits, clé = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- Sur un système d’exploitation 32 bits, clé = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Lorsque la politique de groupe est activée, La clé **HKEY_LOCAL_MACHINE-Software-Policies-Microsoft-VisualStudio-SQM**

::: moniker-end

Entrée et **OptIn**

Valeur = (DWORD)

- **0** est désinvolté (éteindre le VSCEIP)
- **1** est opté (activer le VSCEIP)

> [!CAUTION]
> Une modification incorrecte du Registre peut sérieusement endommager votre système. Avant d'apporter des modifications au Registre, il convient de sauvegarder les données importantes qui se trouvent sur l'ordinateur. Vous pouvez également utiliser **l’option de** démarrage Last Known Good Configuration si vous rencontrez des problèmes après l’application de modifications manuelles.

Pour plus d’informations sur les informations collectées, traitées ou transmises par le programme VSCEIP, consultez la [Déclaration de confidentialité Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Voir aussi

* [Informations de diagnostic collectées par Visual Studio](diagnostic-data-collection.md)
* [Options de commentaires de Visual Studio](../ide/feedback-options.md)
* [Guide pratique pour signaler un problème avec Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/)
* [Déclaration de confidentialité Microsoft](https://privacy.microsoft.com/privacystatement)
