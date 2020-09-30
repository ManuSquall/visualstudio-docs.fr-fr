---
title: 'Meilleures pratiques de développement : COM, VSTO, & les compléments VBA dans Office'
titleSuffix: ''
ms.date: 07/25/2017
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4e536c48004d9c8ff729ac5fb064e04e02c6884b
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91581194"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Meilleures pratiques de développement pour les compléments COM, VSTO et VBA dans Office
  Si vous développez des compléments COM, VSTO ou VBA pour Office, suivez les meilleures pratiques de développement décrites dans cet article.   afin de garantir :

- Compatibilité de vos compléments dans les différentes versions et déploiements d’Office.
- Réduction de la complexité du déploiement des compléments pour les utilisateurs et les administrateurs informatiques.
- Des échecs d’installation ou d’exécution involontaires de votre complément n’ont pas lieu.

>Remarque : l’utilisation du [pont Desktop](/windows/uwp/porting/desktop-to-uwp-root) pour préparer votre complément COM, VSTO ou VBA pour le Windows Store n’est pas prise en charge. Les compléments COM, VSTO et VBA ne peuvent pas être distribués dans le Windows Store ou dans l’Office Store.

## <a name="do-not-check-for-office-during-installation"></a>Ne pas vérifier pour Office pendant l’installation
 Nous vous déconseillons de faire en sorte que votre complément détecte si Office est installé lors du processus d’installation du complément. Si Office n’est pas installé, vous pouvez installer le complément et l’utilisateur pourra y accéder après l’installation d’Office.

## <a name="use-embedded-interop-types-nopia"></a>Utiliser des types Interop incorporés (NoPIA)
Si votre solution utilise .NET 4,0 ou une version ultérieure, utilisez les types Interop incorporés (NoPIA) au lieu de dépendre du package redistribuable des assemblys PIA (Primary Interop Assembly) d’Office. L’utilisation de l’incorporation de type réduit la taille d’installation de votre solution et garantit la compatibilité future. Office 2010 était la dernière version d’Office qui a fourni le package redistribuable PIA. Pour plus d’informations, consultez [procédure pas à pas : incorporation d’informations de type à partir de Microsoft Office assemblys](/previous-versions/ee317478(v=vs.140)) et de l' [équivalence de type et types Interop incorporés](/windows/uwp/porting/desktop-to-uwp-root).

Si votre solution utilise une version antérieure de .NET, nous vous recommandons de mettre à jour votre solution pour utiliser .NET 4,0 ou une version ultérieure. L’utilisation de .NET 4,0 ou version ultérieure réduit les prérequis au moment de l’exécution sur les versions plus récentes de Windows.

## <a name="avoid-depending-on-specific-office-versions"></a>Éviter en fonction des versions spécifiques d’Office
Si votre solution utilise des fonctionnalités qui sont uniquement disponibles dans les versions plus récentes d’Office, vérifiez que la fonctionnalité existe (si possible, au niveau de la fonctionnalité) au moment de l’exécution (par exemple, à l’aide de la gestion des exceptions ou en vérifiant la version). Validez les versions minimales, plutôt que des versions spécifiques, à l’aide d’API prises en charge dans le modèle objet, telles que la [propriété application. version](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>). Nous vous déconseillons de vous reposer sur les métadonnées binaires d’Office, les chemins d’installation ou les clés de Registre, car celles-ci peuvent changer entre les installations, les environnements et les versions.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Activer l’utilisation des bureaux 32 bits et 64 bits
Votre cible de génération par défaut doit prendre en charge à la fois 32 bits (x86) et 64 bits (x64), sauf si votre solution dépend de bibliothèques qui sont uniquement disponibles pour un nombre de bits spécifique. La version 64 bits d’Office croît en cours d’adoption, en particulier dans les environnements Big Data. La prise en charge des versions 32 bits et 64 bits facilite la transition des utilisateurs entre les versions 32 bits et 64 bits d’Office.

Lors de l’écriture de code VBA, utilisez des instructions Declare 64 bits et convertissez les variables appropriées. En outre, assurez-vous que les documents peuvent être partagés entre les utilisateurs qui exécutent des versions 32 bits ou 64 bits d’Office en fournissant du code pour chaque nombre de bits. Pour plus d’informations, consultez [vue d’ensemble de l’Visual Basic 64 bits pour les applications](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Prendre en charge les environnements restreints
Votre solution ne doit pas nécessiter d’élévation de compte d’utilisateur ni de privilèges d’administrateur. En outre, la solution ne doit pas dépendre de la définition ou de la modification :

- Le répertoire de travail actuel
- Répertoires de chargement des DLL.
- Variable de chemin d’accès.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Modifier l’emplacement d’enregistrement des données et des paramètres partagés
Si la solution se compose d’un complément et d’un processus qui est externe à Office, n’utilisez pas le dossier de données d’application ou le registre de l’utilisateur pour échanger des données ou des paramètres entre le complément et le processus externe. Au lieu de cela, envisagez d’utiliser le dossier temporaire de l’utilisateur, le dossier documents ou le répertoire d’installation de votre solution.

## <a name="increment-the-version-number-with-each-update"></a>Incrémenter le numéro de version avec chaque mise à jour
Définissez le numéro de version des fichiers binaires dans votre solution et incrémentez-le à chaque mise à jour. Cela facilitera l’identification des modifications entre les versions et l’évaluation de la compatibilité.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Fournir des instructions de support pour les dernières versions d’Office
Les clients demandent aux ISV de fournir des instructions de prise en charge pour leurs compléments COM, VSTO et VBA qui s’exécutent dans Office. La liste de vos instructions de prise en charge explicite permet aux clients qui utilisent des applications de Microsoft 365 pour Enterprise Readiness de comprendre votre support.

Pour fournir des instructions de prise en charge pour les applications clientes Office (par exemple, Word ou Excel), vérifiez d’abord que vos compléments s’exécutent dans la version d’Office actuelle, puis validez pour fournir des mises à jour si votre complément s’arrête dans une version ultérieure. Vous n’avez pas besoin de tester vos compléments lorsque Microsoft publie une nouvelle version ou une mise à jour d’Office. Microsoft modifie rarement la plate-forme d’extensibilité COM, VSTO et VBA dans Office, et ces modifications sont bien documentées.

>Important : Microsoft gère la liste des compléments pris en charge pour les rapports de disponibilité et les informations de contact ISV. Pour obtenir la liste des compléments, consultez [/ConfigMgr/Desktop-Analytics/Ready-for-Windows](/configmgr/desktop-analytics/ready-for-windows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Utiliser process Monitor pour déboguer les problèmes d’installation ou de chargement
Si votre complément présente des problèmes de compatibilité lors de l’installation ou du chargement, ceux-ci peuvent être liés à des problèmes d’accès aux fichiers ou au registre. Utilisez [Process Monitor](/sysinternals/downloads/procmon) ou un outil de débogage similaire pour consigner et comparer le comportement par rapport à un environnement de travail pour aider à identifier le problème.