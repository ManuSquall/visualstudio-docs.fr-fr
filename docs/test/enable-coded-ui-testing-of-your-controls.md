---
title: Activer le test codé de l'interface utilisateur de vos contrôles
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: ea58dc703c5ad860683017c39d9d37d9b5cccd04
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664945"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Activer les tests codés de l’interface utilisateur de vos contrôles

Implémentez la prise en charge du framework de tests codés de l’interface utilisateur pour rendre votre contrôle plus facile à tester. Vous pouvez ajouter des niveaux croissants de prise en charge de manière incrémentielle. Commencez par permettre la prise en charge de l’enregistrement et de la lecture, ainsi que de la validation de propriété. Ensuite, utilisez cette prise en charge pour permettre au générateur de test codé de l’interface utilisateur de reconnaître les propriétés personnalisées de votre contrôle. Fournissez des classes personnalisées pour accéder à ces propriétés à partir du code généré. Vous pouvez également aider à ce que les actions de capture du générateur de test codé de l'interface utilisateur soient plus proches de l'objectif de l'action en cours d'enregistrement.

![CUIT&#95;Full](../test/media/cuit_full.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="support-record-and-playback-and-property-validation-by-implementing-accessibility"></a>Prendre en charge l’enregistrement et la lecture, ainsi que la validation de propriété, en implémentant l’accessibilité

Le générateur de test codé de l'interface utilisateur capture des informations sur les contrôles qu'il rencontre lors d'un enregistrement et génère ensuite le code pour relire la session. Si votre contrôle ne prend pas en charge l’accessibilité, le générateur de test codé de l’interface utilisateur capture les actions (telles que les clics de souris) à l’aide des coordonnées d’écran. Quand le test est lu, le code généré émet les actions aux mêmes coordonnées d’écran. Si votre contrôle s’affiche à un autre emplacement de l’écran durant la lecture du test, le code généré ne peut pas effectuer l’action. Si vous n’implémentez pas l’accessibilité pour votre contrôle, vous risquez d’observer des échecs de test quand le test est lu sur différentes configurations d’écran, dans différents environnements ou en cas de changement de la disposition de l’IU.

![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png)

Si vous implémentez l’accessibilité, le générateur de test codé de l’interface utilisateur s’en sert pour capturer les informations relatives à votre contrôle quand il enregistre un test. Ensuite, lorsque vous exécutez le test, le code généré relit les événements par rapport à votre contrôle, même s'il se trouve à un autre emplacement de l'interface utilisateur. Les auteurs de tests peuvent également créer des assertions à l’aide des propriétés de base de votre contrôle.

![CUIT&#95;Record](../test/media/cuit_record.png)

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Pour prendre en charge l’enregistrement et la lecture, la validation de propriété et la navigation d’un contrôle Windows Forms
Implémentez l'accessibilité de votre contrôle, comme indiqué dans la procédure suivante et expliqué en détail dans <xref:System.Windows.Forms.AccessibleObject>.

![CUIT&#95;Accessible](../test/media/cuit_accessible.png)

1. Implémentez une classe qui dérive de <xref:System.Windows.Forms.Control.ControlAccessibleObject> et remplacez la propriété <xref:System.Windows.Forms.Control.AccessibilityObject%2A> pour retourner un objet de votre classe.

    ```csharp
    public partial class ChartControl : UserControl
    {
        // Overridden to return the custom AccessibleObject for the control.
        protected override AccessibleObject CreateAccessibilityInstance()
        {
            return new ChartControlAccessibleObject(this);
        }

        // Inner class ChartControlAccessibleObject represents accessible information
        // associated with the ChartControl and is used when recording tests.
        public class ChartControlAccessibleObject : ControlAccessibleObject
        {
            ChartControl myControl;
            public ChartControlAccessibleObject(ChartControl ctrl)
                : base(ctrl)
            {
                myControl = ctrl;
            }
        }
    }
    ```

2. Remplacez les propriétés et méthodes <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> et <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> de l’objet accessible.

3. Implémentez un autre objet d’accessibilité pour le contrôle enfant et remplacez la propriété <xref:System.Windows.Forms.Control.AccessibilityObject%2A> du contrôle enfant pour retourner l’objet d’accessibilité.

4. Remplacez les propriétés et méthodes <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A> et <xref:System.Windows.Forms.AccessibleObject.Select%2A> de l’objet d’accessibilité du contrôle enfant.

> [!NOTE]
> Cette rubrique commence par l’exemple d’accessibilité de <xref:System.Windows.Forms.AccessibleObject>, puis se base dessus pour les procédures qui suivent. Si vous souhaitez créer une version opérationnelle de l’exemple d’accessibilité, créez une application console et remplacez le code de *Program.cs* par celui de l’exemple. Ajoutez des références à Accessibility, System.Drawing et System.Windows.Forms. Changez la propriété **Incorporer les types d’interopérabilité** d’Accessibility en lui affectant la valeur **False** pour éviter un avertissement de build. Vous pouvez changer le type de sortie du projet et remplacer **Application Console** par **Application Windows** pour éviter l’apparition d’une fenêtre de console quand vous exécutez l’application.

## <a name="support-custom-property-validation-by-implementing-a-property-provider"></a>Prendre en charge la validation de propriété personnalisée en implémentant un fournisseur de propriétés

Une fois que vous avez implémenté la prise en charge de base pour l’enregistrement et la lecture, ainsi que pour la validation de propriété, vous pouvez rendre les propriétés personnalisées de votre contrôle accessibles aux tests codés de l’interface utilisateur en implémentant un plug-in <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>. Par exemple, la procédure suivante crée un fournisseur de propriétés qui permet aux tests codés de l’interface utilisateur d’accéder à la propriété State des contrôles enfants CurveLegend du contrôle de graphique :

![CUIT&#95;CustomProps](../test/media/cuit_customprops.png)

### <a name="to-support-custom-property-validation"></a>Pour prendre en charge la validation de propriété personnalisée

![CUIT&#95;Props](../test/media/cuit_props.png)

1. Remplacez la propriété <xref:System.Windows.Forms.AccessibleObject.Description%2A> de l’objet accessible de la légende de la courbe pour passer des valeurs de propriété enrichies dans la chaîne de description. Séparez les valeurs multiples par des points-virgules (;).

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add ";" and the state value to the end
                // of the curve legend's description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

1. Créez un package d’extension de test d’IU pour votre contrôle en créant un projet de bibliothèque de classes. Ajoutez des références à Accessibility, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common et Microsoft.VisualStudio.TestTools.Extension. Modifiez la propriété **Incorporer les types d’interopérabilité** d’Accessibility et attribuez-lui la valeur **False**.

1. Ajoutez une classe de fournisseur de propriétés dérivée de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> :

    ```csharp
    using System;
    using System.Collections.Generic;
    using Accessibility;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        public class ChartControlPropertyProvider : UITestPropertyProvider
        {
        }
    }
    ```

1. Implémentez le fournisseur de propriétés en plaçant les noms de propriété et les descripteurs de propriété dans un <xref:System.Collections.Generic.Dictionary%602>.

1. Substituez <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> pour indiquer que votre assembly fournit une prise en charge spécifique au contrôle pour votre contrôle et ses enfants.

1. Substituez les méthodes abstraites restantes de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>.

1. Ajoutez une classe de package d’extension dérivée de <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Définissez l'attribut `UITestExtensionPackage` pour l'assembly.

1. Dans la classe de package d'extension, substituez <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> pour renvoyer la classe de fournisseur de propriétés lors de la demande d'un fournisseur de propriétés.

1. Substituez les propriétés et méthodes abstraites restantes de <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

1. Créez vos fichiers binaires et copiez-les dans *% ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Ce package d’extension est appliqué à tout contrôle de type « Texte ». Si vous testez plusieurs contrôles du même type, testez-les séparément pour pouvoir gérer les packages d’extension qui sont déployés quand vous enregistrez les tests.

## <a name="support-code-generation-by-implementing-a-class-to-access-custom-properties"></a>Prendre en charge la génération de code en implémentant une classe pour accéder aux propriétés personnalisées

Lorsque le générateur de test codé de l'interface utilisateur génère le code à partir d'un enregistrement de session, il utilise la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> pour accéder à vos contrôles.

Si vous avez implémenté un fournisseur de propriétés pour fournir l’accès aux propriétés personnalisées de votre contrôle, vous pouvez ajouter une classe spécialisée qui permet d’accéder à ces propriétés. L’ajout d’une classe spécialisée simplifie le code généré.

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Pour ajouter une classe spécialisée pour accéder à votre contrôle

![CUIT&#95;CodeGen](../test/media/cuit_codegen.png)

1. Implémentez une classe dérivée de <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> et ajoutez le type de contrôle à la collection de propriétés de recherche du constructeur.

1. Implémentez les propriétés personnalisées de votre contrôle en tant que propriétés de la classe.

1. Substituez la méthode <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> de votre fournisseur de propriétés pour retourner le type de la nouvelle classe de contrôles enfants de la légende de la courbe.

1. Substituez la méthode <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> de votre fournisseur de propriétés pour retourner le type de la méthode PropertyNames de la nouvelle classe.

## <a name="support-intent-aware-actions-by-implementing-an-action-filter"></a>Prendre en charge les actions avec intention en implémentant un filtre d’action

Lorsque Visual Studio enregistre un test, il capture chaque événement de souris et de clavier. Toutefois, dans certains cas, l'objectif de l'action peut se perdre dans la série d'événements de souris et de clavier. Par exemple, si votre contrôle prend en charge la saisie semi-automatique, le même jeu d'événements de souris et de clavier peut entraîner une valeur différente lorsque le test est lu dans un environnement différent. Vous pouvez ajouter un plug-in de filtre d'action qui remplace la série d'événements de clavier et de souris par une seule action. Ainsi, vous pouvez remplacer la série d’événements de clavier et de souris qui permettent de sélectionner une valeur par une action unique qui définit la valeur. Ce remplacement permet de protéger les tests codés de l'interface utilisateur contre les différences de saisie semi-automatique d'un environnement à un autre.

### <a name="to-support-intent-aware-actions"></a>Pour prendre en charge les actions avec intention

![CUIT&#95;Actions](../test/media/cuit_actions.png)

1. Implémentez une classe de filtre d’action dérivée de [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)), en remplaçant les propriétés [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Category](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [Enabled](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Group](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) et [Name](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110)).

1. Remplacez [ProcessRule](/previous-versions/visualstudio/visual-studio-2012/dd987281(v=vs.110)). L’exemple remplace ici une action de double-clic par une action de simple clic.

1. Ajoutez le filtre d'action à la méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> de votre package d'extension.

1. Créez vos fichiers binaires et copiez-les sur *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

> [!NOTE]
> Le filtre d'action ne dépend pas de l'implémentation de l'accessibilité ou du fournisseur de propriétés.

## <a name="debug-your-property-provider-or-action-filter"></a>Déboguer votre fournisseur de propriétés ou filtre d’action

Votre fournisseur de propriété et votre filtre d’action sont implémentés dans un package d’extension. Le générateur de test exécute le package d’extension dans un processus distinct de celui de votre application.

### <a name="to-debug-your-property-provider-or-action-filter"></a>Pour déboguer votre fournisseur de propriétés ou filtre d'action

1. Générez la version de débogage de votre package d’extension, puis copiez les fichiers *.dll* et *.pdb* dans *%ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages*.

2. Exécutez votre application (pas dans le débogueur).

3. Exécutez le test codé de l'interface utilisateur.

     `codedUITestBuilder.exe  /standalone`

4. Attachez le débogueur au processus codedUITestBuilder.

5. Définissez les points d'arrêt dans votre code.

6. Dans le générateur de test codé de l'interface utilisateur, créez des assertions pour tester votre fournisseur de propriétés et enregistrez les actions pour tester vos filtres d'action.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.AccessibleObject>
- [Utiliser l’automatisation de l’interface utilisateur pour tester votre code](../test/use-ui-automation-to-test-your-code.md)