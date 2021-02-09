---
title: Messages d'erreur dans Workflow Designer
description: En savoir plus sur les types de messages d’erreur que vous pouvez rencontrer lors de l’utilisation de Concepteur de flux de travail.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e9e0cc71018d85d91e88d2969e76b49fcf9066a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876574"
---
# <a name="error-messages-in-workflow-designer"></a>Messages d'erreur dans Workflow Designer

Cette rubrique décrit les types de messages d’erreur qui peuvent être rencontrés lors de l’utilisation de Concepteur de flux de travail.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situations dans lesquelles des erreurs se produisent dans Workflow Designer

Les erreurs dans Concepteur de flux de travail se produisent dans les cas suivants :

1. Il existe une erreur dans une expression.

2. Les contraintes de validation d’une activité n’ont pas été satisfaites.

3. Le fichier XAML contient des erreurs qui provoquent l'échec du chargement d'une activité.

4. Le fichier XAML contient des erreurs qui provoquent l'échec du chargement du workflow.

Des expressions non valides et des contraintes de validation non satisfaites n’entraînent pas l’échec de la génération du workflow. La génération de votre flux de travail s’effectue correctement, mais une exception <xref:System.Activities.InvalidWorkflowException> est levée au moment de l’exécution. Si le fichier XAML contient des erreurs, la génération échoue.

Dans Visual Studio, lorsqu’un flux de travail est chargé, ses erreurs sont affichées dans la **liste d’erreurs**. Pour accéder à l’activité qui est la source de l’erreur, double-cliquez sur l’erreur dans la **liste d’erreurs**.

### <a name="expression-errors"></a>Erreurs d'expression
 Une expression non valide est signalée par un point d'exclamation blanc dans un cercle rouge en regard de l'expression. Le déplacement de la souris au-dessus de cette icône affiche une info-bulle qui décrit la source de l'erreur. Dans Visual Studio, cliquez sur l’expression pour afficher la ligne qui souligne la source de l’erreur. Le déplacement de la souris au-dessus du texte souligné affiche une info-bulle qui décrit la source de l'erreur.

### <a name="activity-validation-errors"></a>Erreurs de validation d’activité
 Lorsque les contraintes de validation d’une activité n’ont pas été satisfaites, un point d’exclamation blanc dans un cercle rouge s’affiche dans l’angle supérieur droit de l’activité. Le déplacement de la souris au-dessus de cette icône affiche une info-bulle qui décrit la source de l'erreur.

### <a name="xaml-load-errors"></a>Erreurs de chargement XAML
 En cas d’échec du chargement d’une activité, une zone rouge avec le texte « l’activité n’a pas pu être chargée en raison d’erreurs dans le XAML » s’affiche. Cela se produit généralement lorsque le type de l’activité ne peut pas être résolu. L'activité non valide peut être supprimée dans le concepteur en sélectionnant la zone rouge et en la supprimant.

### <a name="workflow-load-errors"></a>Erreurs de chargement du workflow
 Lorsqu’un flux de travail ne parvient pas à se charger, le texte « Concepteur de flux de travail rencontré des problèmes avec votre document » s’affiche dans l’aire du concepteur, avec les informations sur les exceptions qui ont provoqué le chargement du flux de travail. Cela se produit généralement lorsque le fichier XAML ne peut pas être analysé.
