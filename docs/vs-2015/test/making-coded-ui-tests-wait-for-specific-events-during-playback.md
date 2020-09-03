---
title: Suspension des tests codés de l’interface utilisateur en attendant des événements spécifiques pendant la lecture | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 41981ad6-673e-492e-b739-9863b14157b1
caps.latest.revision: 26
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dbc83731cfc1c04f33fc4de05f28ffd1a54f3e4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851776"
---
# <a name="making-coded-ui-tests-wait-for-specific-events-during-playback"></a>Suspension des tests codés de l'interface utilisateur en attendant des événements spécifiques pendant la lecture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans une lecture de test codé de l'interface utilisateur, vous pouvez faire en sorte que le test attende que certains événements se produisent (par exemple qu'une fenêtre s'affiche, que la barre de progression disparaisse, et ainsi de suite). Pour cela, utilisez la méthode UITestControl.WaitForControlXXX() appropriée, comme décrit dans le tableau suivant. Pour obtenir un exemple de test codé de l’interface utilisateur qui attend l’activation d’un contrôle à l’aide de la <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A> méthode, consultez [procédure pas à pas : création, édition et gestion d’un test codé de l’interface utilisateur](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

 **Configuration requise**

 Visual Studio Enterprise

> [!TIP]
> Vous pouvez également ajouter des délais avant les actions à l'aide de l'éditeur de test codé de l'interface utilisateur. Pour plus d’informations, consultez [Comment : insérer un délai avant une action d’interface utilisateur à l’aide de l’éditeur de test codé de l’interface utilisateur](https://msdn.microsoft.com/library/509f8ef7-e105-4049-b11b-d64549e055b0).

 **UITestControl.WaitForControlXXX(), méthodes**

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>

 Attend que le contrôle soit prêt à accepter une entrée de souris et une entrée au clavier. Le moteur appelle implicitement cette API pour toutes les actions pour attendre que le contrôle soit prêt avant toute opération. Toutefois, bizarrement, vous devez parfois effectuer un appel explicite.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>

 Attend que le contrôle soit activé quand l’Assistant effectue une validation asynchrone de l’entrée via des appels au serveur. Par exemple, vous pouvez imposer à la méthode d’attendre le bouton **Suivant** de l’Assistant avant d’être activée. Pour obtenir un exemple de cette méthode, consultez [procédure pas à pas : création, édition et gestion d’un test codé de l’interface utilisateur](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>

 Attend que le contrôle s'affiche dans l'interface utilisateur. Par exemple, vous attendez une boîte de dialogue d'erreur une fois que l'application a terminé la validation des paramètres. Le temps nécessaire à la validation est variable. Vous pouvez utiliser cette méthode pour attendre la boîte de dialogue d'erreur.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>

 Attend que le contrôle disparaisse de l'interface utilisateur. Par exemple, vous pouvez attendre que la barre de progression disparaisse.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>

 Attend que la propriété spécifiée du contrôle ait la valeur donnée. Par exemple, vous attendez que le texte d’état passe à **Terminé**.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>

 Attend que la propriété spécifiée du contrôle ait la valeur inverse de la valeur spécifiée. Par exemple, vous attendez que la zone d'édition ne soit pas en lecture seule, autrement dit, qu'elle soit modifiable.

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>

 Attend que le prédicat spécifié reprenne la valeur `true`. Cette méthode peut servir pour une opération d'attente complexe (comme des conditions OR) sur un contrôle donné. Par exemple, vous pouvez attendre que le texte d’état soit **Succeeded** ou **Failed**, comme le montre le code suivant :

```csharp

// Define the method to evaluate the condition
private static bool IsStatusDone(UITestControl control)
{
    WinText statusText = control as WinText;
    return statusText.DisplayText == "Succeeded" || statusText.DisplayText == "Failed";
}

// In test method, wait till the method evaluates to true
statusText.WaitForControlCondition(IsStatusDone);

```

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForCondition%2A>

 Toutes les méthodes précédentes sont des méthodes d'instance de UITestControl. Cette méthode est une méthode statique. Cette méthode attend également que le prédicat spécifié soit `true` mais elle peut être utilisée pour une opération d'attente complexe (comme des conditions OR) sur plusieurs contrôles. Par exemple, vous pouvez attendre que le texte d’état soit **Succeeded** ou qu’un message d’erreur s’affiche, comme le montre le code suivant :

```csharp

// Define the method to evaluate the condition
private static bool IsStatusDoneOrError(UITestControl[] controls)
{
    WinText statusText = controls[0] as WinText;
    WinWindow errorDialog = controls[1] as WinWindow;
    return statusText.DisplayText == "Succeeded" || errorDialog.Exists;
}

// In test method, wait till the method evaluates to true
UITestControl.WaitForCondition<UITestControl[]>(new UITestControl[] { statusText, errorDialog }, IsStatusDoneOrError);

```

 Toutes ces méthodes ont le comportement suivant :

 Les méthodes retournent true si l'attente a abouti et false si l'attente a échoué.

 Le délai d'attente implicite de l'opération d'attente est spécifié par  la propriété <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A>. La valeur par défaut de cette propriété s'élève à 60 000 millisecondes (une minute).

 Les méthodes ont une surcharge pour accepter un délai d'attente explicite en millisecondes. Toutefois, quand l'opération d'attente entraîne une recherche implicite du contrôle ou, quand l'application est occupée, le temps d'attente réel peut dépasser le délai d'attente spécifié.

 Les fonctions précédentes sont puissantes et flexibles et doivent répondre à presque toutes les conditions. Toutefois, au cas où ces méthodes ne répondraient pas à vos besoins et que vous devriez coder un <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A> ou un <xref:System.Threading.Thread.Sleep%2A> dans votre code, nous vous recommandons d'utiliser l'API Playback.Wait() au lieu de l'API Thread.Sleep(). Les raisons sont les suivantes :

 Vous pouvez utiliser la propriété <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A> pour modifier la durée de veille. Par défaut, cette variable a la valeur 1, mais vous pouvez l'augmenter ou la réduire pour modifier le temps d'attente dans tout le code. Par exemple, si vous effectuez des tests sur un réseau lent ou dans d'autres circonstances où les performances sont lentes, vous pouvez affecter à cette variable la valeur 1,5 à un seul endroit (ou même dans le fichier de configuration) pour ajouter 50 % d'attente supplémentaire à tous les emplacements.

 Playback.Wait() appelle Thread.Sleep() en interne (après le calcul ci-dessus) en segments plus petits dans une boucle for tout en recherchant une opération cancel\break de l'utilisateur. En d'autres termes, Playback.Wait() vous permet d'annuler la lecture avant la fin de l'attente tandis que la veille risque ou non de lever une exception.

> [!TIP]
> L'éditeur de test codé de l'interface utilisateur vous permet de modifier facilement vos tests codés de l'interface utilisateur. Grâce à lui, vous pouvez rechercher, afficher et modifier vos méthodes de test. Vous pouvez aussi modifier des actions d'interface utilisateur et leurs contrôles associés dans le mappage de contrôle d'interface utilisateur. Pour plus d’informations, consultez [Modification des tests codés de l’interface utilisateur à l’aide de l’éditeur de test codé de l’interface utilisateur](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

 **Assistance**

 Pour obtenir des informations supplémentaires, consultez [Test de la livraison continue avec Visual Studio 2012 - Chapitre 5 : Automatisation des tests système](https://msdn.microsoft.com/library/jj159335.aspx)

## <a name="see-also"></a>Voir aussi
 [Utiliser UI Automation pour tester votre code](../test/use-ui-automation-to-test-your-code.md) [création de tests codés](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) de l’interface utilisateur [procédure pas à pas : création, édition et gestion d’un test codé de l’interface utilisateur](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md) [anatomie d’un test codé de l’interface utilisateur](../test/anatomy-of-a-coded-ui-test.md) [configurations et plateformes pour les tests codés de l’interface utilisateur et enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) [Comment : insérer un délai avant une action d’interface utilisateur à l’aide de l’éditeur de test](https://msdn.microsoft.com/library/509f8ef7-e105-4049-b11b-d64549e055b0)
