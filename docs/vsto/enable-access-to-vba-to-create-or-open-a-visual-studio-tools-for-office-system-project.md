---
title: Accès VBA pour créer/ouvrir un projet système VSTO
titleSuffix: ''
description: Découvrez que vous devez activer explicitement l’accès au système de projet Office VBA avant de pouvoir créer ou ouvrir un projet Visual Studio Tools pour Office System.
ms.custom: seodec18, SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ef68ffccd7a048cd0591ee0bf1aa511fe0489c92
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910511"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Activer l’accès à VBA pour créer ou ouvrir un Visual Studio Tools pour le projet Microsoft Office système

Vous devez activer explicitement l’accès au système de projet Visual Basic pour Applications (VBA) dans Microsoft Office pour pouvoir créer ou ouvrir un Visual Studio Tools pour le projet Microsoft Office système.

 Microsoft Office projets de développement nécessitent l’accès au système de projet Visual Basic pour Applications (VBA) dans Microsoft Office Word et Microsoft Office Excel, même si les projets n’utilisent pas de Visual Basic pour Applications. La prise en charge au moment du design des contrôles dans les projets Visual Basic et C# est liée au système de projet Visual Basic pour Applications.

 Certains virus des macros Microsoft Office tentent d'automatiser le système de projet Visual Basic pour Applications dans le but de se propager. En activant l'accès au système de projet Visual Basic pour Applications, vous supprimez une protection qui empêche les virus des macros de se répandre. Toutefois, la sécurité normale appliquée aux macros reste en place. Ainsi, le niveau de sécurité des macros et la liste des éditeurs approuvés que vous tenez à jour pour vos applications Office déterminent si une macro s'exécute sur votre ordinateur.

> [!NOTE]
> Cela s'applique uniquement à l'ordinateur de développement. Les ordinateurs des utilisateurs finaux n’ont pas besoin de cette option activée pour exécuter des solutions Office.

 Il est important de noter que la désactivation de l'accès au système de projet Visual Basic pour Applications ne protège pas en soi contre les virus, elle vous aide simplement à empêcher certains virus de se répandre dans d'autres documents si votre ordinateur est infecté par un virus de macro. L'option est désactivée par défaut pour apporter une couche supplémentaire de protection à votre ordinateur, mais son activation ne rend pas votre ordinateur plus vulnérable aux virus si vous appliquez les meilleures pratiques en matière de sécurité.

 La meilleure protection contre les virus de macros Office consiste à exécuter Office au niveau de sécurité élevé ou très élevé, pour ne faire confiance qu’aux macros provenant de sources vérifiées et connues, et pour rester à jour avec les correctifs de sécurité et les logiciels antivirus.

 Vous pouvez activer ou désactiver l’option **d’approbation d’accès à Visual Basic projet** manuellement.

 Vous pouvez réparer votre installation Office si des erreurs VBA ou COM s'affichent.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Pour activer ou désactiver l’accès aux projets Visual Basic

1. Cliquez sur l'onglet **Fichier** .

2. Cliquez sur **Options**.

3. Cliquez sur Centre de gestion de la **confidentialité**, puis sur paramètres du centre de gestion de la **confidentialité**.

4. Dans le **Centre** de gestion de la confidentialité, cliquez sur **paramètres des macros**.

5. Cochez ou décochez **l’option approuver l’accès au modèle objet de projet VBA** pour activer ou désactiver l’accès aux projets Visual Basic.

6. Cliquez sur **OK**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>Pour activer ou désactiver l’accès aux projets Visual Basic avec le système 2007 Microsoft Office

1. Dans le menu **Outils** de Word ou Excel, pointez sur **macro**, puis cliquez sur **sécurité**.

2. Dans la boîte de dialogue **sécurité** , cliquez sur l’onglet **éditeurs approuvés** .

3. Activez ou désactivez cette option pour autoriser **l’accès à Visual Basic projet**.

4. Cliquez sur **OK**.

## <a name="to-set-your-office-macro-security-level"></a>Pour définir le niveau de sécurité des macros Office

1. Cliquez sur l'onglet **Fichier** .

2. Cliquez sur **Options**.

3. Cliquez sur Centre de gestion de la **confidentialité**, puis sur paramètres du centre de gestion de la **confidentialité**.

4. Dans le **Centre** de gestion de la confidentialité, cliquez sur **paramètres des macros**.

5. Dans la section paramètres de la **macro** , sélectionnez le paramètre souhaité.

6. Cliquez sur **OK**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Pour définir le niveau de sécurité des macros Office avec le système 2007 Microsoft Office

1. Dans le menu **Outils** de Word ou Excel, pointez sur **macro**, puis cliquez sur **sécurité**.

2. Sous l’onglet **niveau de sécurité** , sélectionnez le paramètre souhaité.

    L’onglet **niveau de sécurité** contient des détails sur chaque niveau. Pour plus d'informations, voir la rubrique « Niveaux de sécurité des macros » dans l'aide Office.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>Pour installer VBA avec le système Microsoft Office 2007

1. Dans le panneau de configuration, exécutez **Ajout/suppression de programmes** ou **programmes et fonctionnalités**.

2. Sélectionnez Office dans la liste **programmes actuellement installés** .

3. Cliquez sur **Modifier**.

4. Sélectionnez **Ajouter ou supprimer des fonctionnalités**, puis cliquez sur **Continuer**.

5. Sélectionnez **choisir la personnalisation avancée des applications**, puis cliquez sur **suivant**.

6. Développez **composants partagés d’Office** dans la liste **Choisissez les options de mise à jour pour les applications et les outils** .

7. Ouvrez le menu déroulant en regard de **Visual Basic pour applications**, puis cliquez sur **exécuter à partir de poste de travail**.

8. Cliquez sur **Continuer**.

9. Cliquez sur **Fermer**.

## <a name="to-repair-your-installation-of-office"></a>Pour réparer votre installation d'Office

1. Dans le panneau de configuration, exécutez **Ajout/suppression de programmes** ou **programmes et fonctionnalités**.

2. Sélectionnez votre version d’Office dans la liste **programmes actuellement installés** .

3. Cliquez sur **Modifier**.

4. Sélectionnez **réinstaller ou réparer**, puis cliquez sur **suivant**.

5. Sélectionnez **détecter et réparer les erreurs dans mon installation Office**, puis cliquez sur **installer**.

## <a name="see-also"></a>Voir aussi
- [Sécuriser les solutions Office](../vsto/securing-office-solutions.md)
