---
sidebar_position: 1
---

# 🟢 Wstęp

W tym rozdziale omówiono, jak zwiększyć wiarygodność uzupełnień oraz jak
jak wdrożyć kontrole, aby upewnić się, że dane wyjściowe są wiarygodne.

W pewnym stopniu większość
większość poprzednich technik, o których mowa, ma związek z poprawą dokładności uzupełniania
dokładności, a tym samym niezawodności, w szczególności self-consistency(@wang2022selfconsistency).
Istnieje jednak szereg innych technik, które można wykorzystać do poprawy niezawodności,
poza podstawowymi strategiami podpowiadania.

%%LLMs|LLM%% wykazują różne problemy, w tym halucynacje(@webson2023itscomplicated),
błędne wyjaśnienia za pomocą metod %%CoT|CoT prompting%%(@ye2022unreliability), oraz wiele błędów (bias).
w tym majority label bias, recency bias i common token bias(@zhao2021calibrate).
Dodatkowo, zero-shot CoT może być szczególnie stronniczy, gdy mamy do czynienia z wrażliwymi tematami
(@shaikh2022second).

Wspólne rozwiązania niektórych z tych problemów obejmują kalibratory do usuwania uprzedzeń,
i weryfikatorów do oceny uzupełnień, jak również promowanie różnorodności w uzupełnieniach.


