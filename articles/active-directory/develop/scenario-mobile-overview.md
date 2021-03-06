---
title: Web API を呼び出すモバイル アプリの構築 | Azure
titleSuffix: Microsoft identity platform | Azure
description: Web API を呼び出すモバイル アプリを構築する方法 (概要) について説明します
services: active-directory
author: jmprieur
manager: CelesteDG
ms.service: active-directory
ms.subservice: develop
ms.topic: conceptual
ms.workload: identity
ms.date: 05/07/2019
ms.author: jmprieur
ms.reviewer: brandwe
ms.custom: aaddev, identityplatformtop40
ms.openlocfilehash: 1f90f7f23fbdf10b91d8dfc7cd00cca83cd32fbc
ms.sourcegitcommit: d187fe0143d7dbaf8d775150453bd3c188087411
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80882575"
---
# <a name="scenario-mobile-application-that-calls-web-apis"></a>シナリオ:Web API を呼び出すモバイル アプリケーション

Web API を呼び出すモバイル アプリを構築する方法について説明します。

## <a name="prerequisites"></a>前提条件

[!INCLUDE [Prerequisites](../../../includes/active-directory-develop-scenarios-prerequisites.md)]

## <a name="getting-started"></a>作業の開始

最初のモバイル アプリケーションを作成して、クイック スタートをお試しください。

> [!div class="nextstepaction"]
> [クイック スタート: Android アプリからトークンを取得し、Microsoft Graph API を呼び出す](./quickstart-v2-android.md)
>
> [クイック スタート: iOS アプリからトークンを取得し、Microsoft Graph API を呼び出す](./quickstart-v2-ios.md)
>
> [クイック スタート: Xamarin iOS および Android アプリからトークンを取得し、Microsoft Graph API を呼び出す](https://github.com/Azure-Samples/active-directory-xamarin-native-v2)

## <a name="overview"></a>概要

パーソナライズされたシームレスなユーザー エクスペリエンスはモバイル アプリにとって必要不可欠です。  Microsoft ID プラットフォームを使用すれば、モバイル開発者は iOS および Android のユーザーに対してこのエクスペリエンスを作り出すことができます。 アプリケーションで、Azure Active Directory (Azure AD) ユーザー、個人の Microsoft アカウント ユーザー、Azure AD B2C ユーザーをサインインさせることができます。 また、ユーザーに代わって Web API を呼び出すためのトークンを取得することもできます。 これらのフローを実装するには、Microsoft Authentication Library (MSAL) を使用します。 MSAL では、業界標準の [OAuth 2.0 承認コード フロー](v2-oauth2-auth-code-flow.md)を実装しています。

![デーモン アプリ](./media/scenarios/mobile-app.svg)

モバイル アプリに関する考慮事項:

- **ユーザー エクスペリエンスが重要**:ユーザーにサインインを要求する前に、アプリの価値がわかるようにします。 必要なアクセス許可のみを要求します。
- **すべてのユーザー構成をサポート**:多くのモバイル ビジネス ユーザーは、条件付きアクセス ポリシーとデバイス コンプライアンス ポリシーに従う必要があります。 必ずこれらの重要なシナリオをサポートしてください。
- **シングル サインオン (SSO) の実装**:MSAL と Microsoft ID プラットフォームを使用すると、デバイスのブラウザーまたは Microsoft Authenticator (および Android の Intune ポータル サイト) を介したシングル サインオンを実現できます。
- **共有デバイス モードの実装**: 病院、製造、小売、財務などの共有デバイス シナリオで、アプリケーションを使用できるようにします。 [共有デバイス モードのサポートに関する詳細をご覧ください](msal-shared-devices.md)。

## <a name="specifics"></a>詳細

Microsoft ID プラットフォームでモバイル アプリを構築するときは、以下の考慮事項を念頭に置いてください。

- プラットフォームによっては、ユーザーが初めてサインインするときにユーザーの操作が必要になる場合があります。 たとえば iOS では、Microsoft Authenticator (および Android の Intune ポータル サイト) を介して初めて SSO を使用するときに、アプリでユーザーの操作を表示する必要があります。
- iOS および Android 上の MSAL で、外部ブラウザーを使用してユーザーをサインインさせることができます。 外部ブラウザーをアプリ上に表示できます。
- モバイル アプリケーションでは、シークレットは決して使用しないでください。 これらのアプリケーションでは、すべてのユーザーがシークレットにアクセスできます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [アプリの登録](scenario-mobile-app-registration.md)
