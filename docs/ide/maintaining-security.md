---
title: Gestion de la sécurité des applications dans Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- unauthorized access
- Baseline Security Analyzer
- Microsoft Baseline Security Analyzer
- security [.NET Framework], best practices
- MBSA (Microsoft Baseline Security Analyzer)
- security [.NET Framework], maintaining after deployment
ms.assetid: 621d10c1-842b-4902-be60-bb9719591751
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fb75bfe3c9e479e67c766137ee84e919f9a6710
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="maintaining-security"></a>Gestion de la sécurité

On dit souvent qu'une vigilance permanente est le prix à payer pour bénéficier de la sécurité. Malgré toute l'attention que vous avez pu donner à la sécurité au cours des phases de conception et de développement de votre application, vous devez supposer que des défauts de sécurité surviendront après son déploiement. En auditant votre application et en analysant les journaux des événements, vous risquez de découvrir des défauts jusque-là masqués.

D'autre part, vous devez non seulement rester vigilant sur votre propre application, mais aussi vous tenir informé des menaces et des défauts de sécurité de la plateforme sur laquelle votre application s'exécute et des autres produits dont dépend votre application.

[Sécurité, confidentialité et comptes](https://support.microsoft.com/products/microsoft-account?category=privacy#security-privacy-accounts-help=windows-8&v0h=winrttab1&v1h=win8tab1&v2h=win7tab1&v3h=winvistatab1)&mdash;Obtenez de l’aide sur la sécurité, la confidentialité et les comptes d’utilisateur, notamment des informations sur les virus, les mots de passe, les paramètres de contrôle parental, les pare-feu et le chiffrement de lecteur.

[Bulletins relatifs aux mises à jour de sécurité Microsoft](https://technet.microsoft.com/security/bulletins.aspx)&mdash;Cette page facilite la recherche des bulletins publiés. Destinés aux professionnels de l'informatique, les bulletins de sécurité fournissent des informations détaillées sur les mises à jour de la sécurité.

[Microsoft Baseline Security Analyzer](https://www.microsoft.com/download/details.aspx?id=7558)&mdash;MBSA (Microsoft Baseline Security Analyzer) est un outil qui permet à un utilisateur privé, un utilisateur professionnel ou un administrateur d’analyser un ou plusieurs ordinateurs Windows pour rechercher les erreurs usuelles de configuration de la sécurité.