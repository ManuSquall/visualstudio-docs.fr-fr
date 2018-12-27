---
title: Activer l’accès au code VBA pour créer ou ouvrir un Visual Studio Tools pour Microsoft Office system project
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office system project
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1b1a7be701c9bec45011980ced63051150579ca7
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647568"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Activer l’accès au code VBA pour créer ou ouvrir un Visual Studio Tools pour Microsoft Office system project

Vous devez activer explicitement l’accès à Visual Basic pour le système de projet d’Applications (VBA) dans Microsoft Office avant de pouvoir créer ou ouvrir un Visual Studio Tools pour Microsoft Office system project.

 Les projets de développement Microsoft Office requièrent l’accès à Visual Basic pour le système de projet d’Applications (VBA) dans Microsoft Office Word et Microsoft Office Excel, même si les projets n’utilisent pas Visual Basic pour Applications. La prise en charge au moment du design des contrôles dans les projets Visual Basic et C# est liée au système de projet Visual Basic pour Applications.

 Certains virus des macros Microsoft Office tentent d'automatiser le système de projet Visual Basic pour Applications dans le but de se propager. En activant l'accès au système de projet Visual Basic pour Applications, vous supprimez une protection qui empêche les virus des macros de se répandre. Toutefois, la sécurité normale appliquée aux macros reste en place. Ainsi, le niveau de sécurité des macros et la liste des éditeurs approuvés que vous tenez à jour pour vos applications Office déterminent si une macro s'exécute sur votre ordinateur.

> [!NOTE]
> Cela s'applique uniquement à l'ordinateur de développement. Ordinateurs des utilisateurs finaux n’avez pas besoin d’activer cette option pour exécuter des solutions Office.

 Il est important de noter que la désactivation de l'accès au système de projet Visual Basic pour Applications ne protège pas en soi contre les virus, elle vous aide simplement à empêcher certains virus de se répandre dans d'autres documents si votre ordinateur est infecté par un virus de macro. L'option est désactivée par défaut pour apporter une couche supplémentaire de protection à votre ordinateur, mais son activation ne rend pas votre ordinateur plus vulnérable aux virus si vous appliquez les meilleures pratiques en matière de sécurité.

 La meilleure protection contre les virus de macro est d’exécuter Office sur le niveau de sécurité élevé ou très élevé, d’approuver uniquement les macros de vérifié, les sources connues, de bureau et à rester à jour avec les correctifs de sécurité et d’analyse antivirus.

 Pour plus d’informations sur la protection de votre PC contre les virus et autres programmes malveillants, consultez [ http://www.microsoft.com/protect ](http://www.microsoft.com/protect).

 Vous pouvez activer ou désactiver l’option **approuver l’accès au projet Visual Basic** manuellement.

 Vous pouvez réparer votre installation Office si des erreurs VBA ou COM s'affichent.

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Pour activer ou désactiver l’accès aux projets Visual Basic

1. Cliquez sur l'onglet **Fichier** .

2. Cliquez sur **Options**.

3. Cliquez sur **centre de confidentialité**, puis cliquez sur **paramètres Trust Center**.

4. Dans le **centre de confidentialité**, cliquez sur **paramètres des macros**.

5. Activez ou désactivez **faire confiance au modèle d’objet du projet VBA** pour activer ou désactiver l’accès aux projets Visual Basic.

6. Cliquez sur **OK**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>Pour activer ou désactiver l’accès aux projets Visual Basic avec Microsoft Office system 2007

1. Sur le **outils** menu dans Word ou Excel, pointez sur **Macro**, puis cliquez sur **sécurité**.

2. Dans le **sécurité** boîte de dialogue, cliquez sur le **éditeurs approuvés** onglet.

3. Sélectionnez pour activer ou désactiver pour désactiver, **approuver l’accès au projet Visual Basic**.

4. Cliquez sur **OK**.

## <a name="to-set-your-office-macro-security-level"></a>Pour définir le niveau de sécurité des macros Office

1. Cliquez sur l'onglet **Fichier** .

2. Cliquez sur **Options**.

3. Cliquez sur **centre de confidentialité**, puis cliquez sur **paramètres Trust Center**.

4. Dans le **centre de confidentialité**, cliquez sur **paramètres des macros**.

5. Dans le **paramètres des macros** , sélectionnez le paramètre souhaité.

6. Cliquez sur **OK**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Pour définir le niveau de sécurité Office avec Microsoft Office system 2007

1. Sur le **outils** menu dans Word ou Excel, pointez sur **Macro**, puis cliquez sur **sécurité**.

2. Sur le **au niveau de sécurité** , sélectionnez le paramètre souhaité.

    Le **au niveau de sécurité** onglet contient des détails sur chaque niveau. Pour plus d'informations, voir la rubrique « Niveaux de sécurité des macros » dans l'aide Office.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>Pour installer VBA avec le système Microsoft Office 2007

1. Dans le panneau de configuration, exécutez **Ajout / Suppression de programmes** ou **programmes et fonctionnalités**.

2. Sélectionnez Office dans le **programmes actuellement installés** liste.

3. Cliquez sur **Modifier**.

4. Sélectionnez **ajouter ou supprimer des fonctionnalités**, puis cliquez sur **continuer**.

5. Sélectionnez **choisir la personnalisation avancée des applications**, puis cliquez sur **suivant**.

6. Développez **composants partagés d’Office** dans le **choisir les options de mise à jour pour les applications et outils** liste.

7. Ouvrez le menu déroulant à côté **Visual Basic pour Applications**, puis cliquez sur **exécuter à partir du poste de travail**.

8. Cliquez sur **Continuer**.

9. Cliquez sur **Fermer**.

## <a name="to-repair-your-installation-of-office"></a>Pour réparer votre installation d'Office

1. Dans le panneau de configuration, exécutez **Ajout / Suppression de programmes** ou **programmes et fonctionnalités**.

2. Sélectionnez votre version d’Office dans le **programmes actuellement installés** liste.

3. Cliquez sur **Modifier**.

4. Sélectionnez **réinstaller ou réparer**, puis cliquez sur **suivant**.

5. Sélectionnez **détecter et réparer les erreurs dans mon installation Office**, puis cliquez sur **installer**.

## <a name="see-also"></a>Voir aussi

 [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)