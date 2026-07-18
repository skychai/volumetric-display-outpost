
# Day 1 7/15/26: Exploring concept, spent 4 hours

I researched some volumetric display projects, looked at rotational vs linear approaches.
Decided to go with rotational, with panels arranged on both sides like this:

<img width="302" height="212" alt="image" src="https://github.com/user-attachments/assets/855b48f7-7c3a-4c21-abae-07734ae6d563" />


Then I identified the base components:
- high wattage power source
- strong motor
- LED matrices
- encoder (photoresistor?)
- microcontroller w/ wifi capability
- slip ring?




# Day 2 7/16/26: Selecting parts, spent 3 hours

I decided to prioritize the schematic over CAD since getting electronics to work in sync will be the main challenge.

First, I went back to select the specific components that will work together. After reviewing power requirements, I decided to go ahead with two 32x64 LED matrices. Additionally, I decided to reduce the project complexity by getting rid of the encoder plan to sync up frames, instead opting for a highly accurate stepper motor, and I chose a NEMA 17. The motor's accuracy will enable precise frame sync with rotation without needing the onboard microcontroller to verify the position.

Then I chose a power source that will be able to supply both the motor and the display. I estimated a max draw of 2 amps from the motor (operating at 12V), and 5 amps from the LED matrices (operating at 5V). This makes a 12V 60W power supply very feasible for this project, and I'll use a step-down converter to get the voltage down to 5V for the rest of the components.

# Day 3 7/17/26: Finalizing schematic, spent 2 hours

I revisited my parts list and found suitable products.

BOM:
- [12V 60W wall power supply](https://www.amazon.com.au/BQLZR-Hattype-Capsule-Electronic-Equipment/dp/B01CJJNL46ttps://www.amazon.com/LLTOP-Waterproof-AC100-264V-Transformer-Computer/dp/B088GYYNGG/ref=sxin_19_pa_sp_search_thematic_sspa?content-id=amzn1.sym.292df443-b323-44ae-8b40-9a666975b8b5%3Aamzn1.sym.292df443-b323-44ae-8b40-9a666975b8b5&cv_ct_cx=60w%2B12v%2Bpower%2Bsupply&keywords=60w%2B12v%2Bpower%2Bsupply&pd_rd_i=B088GYYNGG&pd_rd_r=c0881959-0fff-4098-8912-45f76cae51c3&pd_rd_w=7U8Ab&pd_rd_wg=2AR5g&pf_rd_p=292df443-b323-44ae-8b40-9a666975b8b5&pf_rd_r=1PBJ5HK5AQ2MQP6HK9DF&qid=1784353678&sbo=RZvfv%2F%2FHxDF%2BO5021pAnSA%3D%3D&sr=1-2-6024b2a3-78e4-4fed-8fed-e1613be3bcce-spons&aref=zyC9MXZd8O&sp_csd=d2lkZ2V0TmFtZT1zcF9zZWFyY2hfdGhlbWF0aWM&th=1)
- [step-down converter]([url](https://www.amazon.com/Klnuoxj-Converter-Reduced-Voltage-Regulator/dp/B0CRVWDVHG?th=1))
- [NEMA 17 integrated stepper motor]([url](https://www.amazon.com/YEJMKJ-Stepper-Integrated-58-06oz%C2%B7-Controller/dp/B0FHHSQN99/ref=sr_1_2?crid=3UNSOQRQPY3DJ&dib=eyJ2IjoiMSJ9.RxJOI_f7x2ECHbwzUJtNHkscBPWby5sxDoxLuhNxzfaPBTg22krMBPNWaHcZ3w_zItZFQVdtWW_XDhah2yJaENdjb8QDrZbAsKfRZZx-LTSnbMuZ7XaWx-CBOqX11NqHHpPy1n3xs_1ifZ0DPPPiL4RRmDkWer-eyf5eYWSOgoQGWsz5-HAsmbjY0qOkirT8bZfVBQdh3rJnJNYPDPo-v63_4MDTV5KP7Y9jvT0OkBY.7xid49GrDX5zC6kpgw43QPCYaPMQ2G1USvOZFjpQDcg&dib_tag=se&keywords=stepper+motor+integrated+driver&qid=1784325900&sprefix=stepper+motor+integrated+dri%2Caps%2C277&sr=8-2))
- [10A slip ring](- [12V 60W wall power supply]([url](hhttps://www.amazon.com.au/BQLZR-Hattype-Capsule-Electronic-Equipment/dp/B01CJJNL46ttps://www.amazon.com/LLTOP-Waterproof-AC100-264V-Transformer-Computer/dp/B088GYYNGG/ref=sxin_19_pa_sp_search_thematic_sspa?content-id=amzn1.sym.292df443-b323-44ae-8b40-9a666975b8b5%3Aamzn1.sym.292df443-b323-44ae-8b40-9a666975b8b5&cv_ct_cx=60w%2B12v%2Bpower%2Bsupply&keywords=60w%2B12v%2Bpower%2Bsupply&pd_rd_i=B088GYYNGG&pd_rd_r=c0881959-0fff-4098-8912-45f76cae51c3&pd_rd_w=7U8Ab&pd_rd_wg=2AR5g&pf_rd_p=292df443-b323-44ae-8b40-9a666975b8b5&pf_rd_r=1PBJ5HK5AQ2MQP6HK9DF&qid=1784353678&sbo=RZvfv%2F%2FHxDF%2BO5021pAnSA%3D%3D&sr=1-2-6024b2a3-78e4-4fed-8fed-e1613be3bcce-spons&aref=zyC9MXZd8O&sp_csd=d2lkZ2V0TmFtZT1zcF9zZWFyY2hfdGhlbWF0aWM&th=1)))
- [2x LED 32x64 matrix]([url](https://www.amazon.com/waveshare-Full-Color-Adjustable-Brightness-Compatible/dp/B0BQYDLHY9/ref=sr_1_1?crid=2592P0IUPA9W8&dib=eyJ2IjoiMSJ9.wPjGB83y1dRO2t_g5qkiumo8Fj_Z3R5Naq5QkoC0S0AkXSxXhkmG_IxkEVAJaHGBo0_06rvBugrSvHY2SSkdqeLFRioIl8cc4TGHwOHrYZNVb81RMa7k83qLkyXMtVPAfC-fzdFIMla4yeYXsvnbl1WvYMzlMlinY_6Yy3NlEwXtz_NfeNGwZjadTm6G1X-cFCoPdKLiXDED8KNsanjHYsKp2wMjQnK-59eHTlo4gLs.D1lLhud8yF06obfTvU3Y9FTYWV6JAUkxT26dw7WFKK4&dib_tag=se&keywords=32x64+led+matrix&qid=1784326462&sprefix=32x64+led+matr%2Caps%2C270&sr=8-1))
- [2x ESP32 w/ crimp breakout]([url](https://www.amazon.com/AITRIP-ESP-WROOM-32-Bluetooth-ESP32-DevKitC-32-Development/dp/B0DNFN7FHD/ref=sr_1_4?crid=2ILVJO0ATP6MD&dib=eyJ2IjoiMSJ9.Y4sDvn282eRfLalsrj0oa1WqHtcW5nglFLoRqp7MEsW3y6hLA_Iop4-U_cHphZXrQ2rjFoDJ4cMQE43xKIVvVsB58f0CNLAM656c8ouBqOtjZIqDTXeeZ7X1U6Y8Lq44g-q5Pbxm5I9Q_Ea0U1rWk1S-4FRuqSf3g1WyMSa_DXIos1_TG25W_IDs0DvCRWGSXEXfLDmQ73Min9bSi1iZpBWwVJT27jg4mVSiq9OA6Jk.JAPPBebVVFisdPTKrh5nVqwQMi32ZAh3_NEyLmBvg8w&dib_tag=se&keywords=ESP32%2B2%2Bpack%2B38%2Bpin&qid=1784354453&sprefix=esp32%2B2%2Bpack%2B38%2Bpin%2Caps%2C112&sr=8-4&th=1))
