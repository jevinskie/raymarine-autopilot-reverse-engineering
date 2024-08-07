# raymarine-autopilot-reverse-engineering
Notes and tools for reverse engineering Raymarine autopilot systems

## Autopilot Components
### EV-1 Evolution autopilot Sensor Core
 - General component name: CCU
 - SKU: E70096
 - SoC: [STM32F4](https://www.st.com/en/microcontrollers-microprocessors/stm32f4-series.html)
 - Core: Cortex-M4 [HTML](https://developer.arm.com/documentation/100166/0001/) [PDF](https://documentation-service.arm.com/static/5fce431be167456a35b36ade) [archive.org link](https://web.archive.org/web/20230430053918/https://documentation-service.arm.com/static/5fce431be167456a35b36ade) (ARMv7E-M)
 - Firmware (ISO) URL: [`https://flir.app.box.com/public/static/db9m0mkx4wtsaygvw0m728btquubtxt4.zip`](https://flir.app.box.com/public/static/db9m0mkx4wtsaygvw0m728btquubtxt4.zip) -> [`https://flir.app.box.com/public/static/db9m0mkx4wtsaygvw0m728btquubtxt4.zip`](https://flir.app.box.com/public/static/db9m0mkx4wtsaygvw0m728btquubtxt4.zip) -> [`https://public.boxcloud.com/d/1/b1!<barf-removed>../download`](https://public.boxcloud.com/d/1/b1!cCni6DY3Sfi7EWZkmL6DRORQvmjybdbHb-u75RVYbMCBIY2iHhwEXi08Y-AKKdyBSEbwSY2A9q9JtMgj3rTYr8w59gp9MdlKY08KutV7I2rwpo-zsNaHgg6r_Gb1mQlu7H4pEaME9UU8NCt7MGAqWiMsoFN4xxaz_FDa0hCkl1mNXYmeV53WUH_FF6mWrDXyJWJY9HZYKYqJYW_o4T0l4mgGrzxylOU0qOeLV5ln2MRkj7kTxQ6we9fGwcTZpuwsH5GSwBKJNB6Z0j1JDOpf0vbQ9X_D9fLRgXGkcuO3D63-GAiXxtw3cAnW0TM0PsKY_8C0pauXxRkYv-j6tD2v-ABSrxcwJgWu5Y2EoPViB44NKCTPY-l0GTaDE5Rc21_xamJ1yMLxJOnN5rAvN_5dp4c4wguOlGbRpTl29hDzn5BNjE-sqlk4cIpR3E3HO_BS1E7Cn79PwJsQWr5QwHgMU2Oddt1mQDc4hlwUl_5YvbCkc5foB41Gu1TBmOxLm9V7_fdTPIcCuUB9OvVR9fxkk9w67x7QvPwiR3Jnc4H_T9XAZQRKbHNXFuWqTZRkd-yaFgGN6MccJVBxbu2-5OxEjN3mvND8EvESO6u__Ae4HUUeNxuKqo3JZCdUHh8OcMWtGVtI-yOpd06szzO0OBXB3vyNzZGimCnaTd9BHK5AzzDPafASuVkRICQWN1BasHxzU6OTiyLfzxTDp7whNjFa0_FVhOaFdSeOzo0G-5JIsoeZuCE0SnN0q5XEydvm1S79Mp1t_4-3O4Lo9ZYH_Qfuvnp2pYtkyCC0ISEu1hg8GBnSFvJGPtOWbpycPsC88MJ1aE9Os-jKixX2PCT2ZlHM_7E-Gpr2v11Eqsl0mN36u0BFSRRJOq_VJccc4Iz25u04cW6XqIIbAIFuharcYUeOjFMAVR8YT7rMmXkAkmguDQ0Oh-1b__GXgebgh4PiSLfMGZfkWfThTiweVdmTPGdyT3a6c07tF73hM0FZjJMwfUw8WSdcIjNuOMlwfbMdRmJPyjip1aOvqMzsiRkgDGMKnb8PyGIv5MbpcHgpu10rfMGfEQnVDCywETQB2ft2spVgj1K3EOPCqrLJvAGxcNfZMtxSlpoydkY7A_OIhb6WO2dFlXT9c7byDYOLUA8pAts2NdfHq19Wm0cHRvMaiSsHJtOiSLzKubQNmd7Fo2_814x12xdttBfoTN-RhIITpc31l-7sk5CCv8834hy3BOR3cIy3lrKKviZS0uNplH_6GthGMsdoIaaW_QOV6Q5TofiRwuPSOkUvc4QUQEZx4ykKuHUS4N92ao69oTd2wd4jH9qogpFxToF_gWhV4JHCflTxtISo28DQxD-kRbPhSYbFtPIIubflHIvLfQcwPb7PR8SXK0zkhNzI-M8Iki7V7_aj6w../download) [archive.org link](https://web.archive.org/web/20240807015659/https://public.boxcloud.com/d/1/b1!SdHrC7eyPBlziiN4fORhnnNJqD6Phup9qPLQB8zvK9KGylI8g1rEEqFLPpnyfnFBrVC7NtZzkGJ3ROlEz-R_MXAvaI1mNgyj1qwwMeMv1ilO87KQj0nafaj-PExW6lzWZ2OzL_cfZ-52wWtcWQUB3aBXcFjmPEvbgF2eUsjxExHTrSCQIVqJWEOWWt85A8SCn7v7Iv_8hsHh79zs7mluwkCh82V-kl8j5smpEPJbMC9J-49ISqVtmSZsN4bZHqmkvKu3dd-a2hZV0M_xP87IunuXvF2J1PXk48C8tu9KgT1GZPiDizgqJvig2-ZlQ5NpUgPhdklZftl9EsqyzSm3_B0fUl3jFROb38nfFs9MQ-Oi3vUbjyRAxInaTlQeZdOEpRApxtoqhj8YM6rgHvYPxf-5DIKavVQdUOGxE9CXoySrnvpi15BBLGuJ25KHLFGo8COa-XvxtAt1vWXp3r51HJV-_Sr6cu7Dk1D4XtDllk_R4fC-OuEFquUXJnfPJQ5VfEsrQtvVytVGZrMeLtqlE6lP7ZRIAf-MScv68PNJ1L-9d-pxmPBu8ivLb2_L9XaybRCcNDQsWMrFf3YqdyLGuZn9NJND0ydlEdb31efntX-avyIJOdHNNcvVLo1TFMPB-T1sAMf0egXt6ab7oHn1RMXHYiCVsqxkDUnM8L6or2VHIzzZmiybIcbIYmx_mZ-ZzKTHkhmmiNUcuroCza6-0AZDCG29SYd2H33GZ9iVoQUi2VINF37mLSh5yRZZwHFDmZCdqyvdTdLEkTMhN2olhbzPR3xqp94Fn0liE2t1H4fsm1dJrUxoBxC8d9nSIDZp2ZMuwxuYH1CbY2Vr97joxlb5Zzo5azNyIzTdc3OpwEuEqxWpRr_oF-qWHQ61JfYjlIjpJJ7hT4dHt_6glpg1VU9cbs1rm0NxmhMGuKFJODXofGHnRSkm5yQFpya1Reo4_SjAVJPxMJSId9ctLaB4NDJvM1hMpijhasRoUQFnd7HXF2K-0JhIN-vnMXzOIqmWBceZVr8e_J1Bd5Pvf82gX3l0Ee0R18a4JE4dTE6jII2TWKdz5Kn9puPQqVHwO_wyLaIcRhMQL8aRU-9XYtz_vjsIvb_P6OlIiiJJXYSxin1c_veSTeBTL34JomsqX0qeYJqwOqyATBkGu-L9gkRCsSprT-jLCoKXJEmqP4TNJtyVdiAh3JOXgDg9eiY7v8B2LSRYGjxxtP9FQCvxp3wum0CWgd2KCc-c7YL_om_rsnDneXENxqGhkzwkWUfClCsdzM463xp4jKEq6rO9VSV0Z9PX-0b9Hxpbdz_5IHx6LULFMz_eaeRV3hYAIblV_b989VSiskSbvHSiRPaQgTFkO6hFg3hTkj3iLhxa2WHL9fO_s2eVH3ZrNyHNxPr-bZQhO2I./download)
 - Firmware ISO ZIP filename: `ray_Pilots-Web.upgrade.zip`
 - Firmwre ISO ZIP SHA-256: `912c2aa4e272ef86e98572c083e55e9170f68f9d0a56228dc34a971b9c8fb07e`
 - Firmware ISO filename: `ray_p70v313_CCUv317_ACUv313_ACUF2v315.upgrade.iso`
 - Firmware ISO SHA-256: `2b8f37890f38d93587e59268524e19eea6ce2c12b07d1ad23a7df2765d901d03`
 - Firmware ISO `manifest.xml` SHA-256: `9428381f6d498be303edaa375e614d062858c1c8a135b9f727310541490e7c6c`
 - Firmware PKG filename: `CCU_3.17Release.pkg`
 - Firmware PKG SHA-256: `e61889a01011c8cab02606d92bb72c177067a751b7ca5c86b8bc5acd89de0217`
 - Firmware version: 3.17
 - Firmware release date: 2024-02
 - Firmware build date: 2024-02-27
 - Firmware OS: FreeRTOS

### ACU-100 Evolution autopilot Actuator Control Unit
 - SKU: E22167
 - General component name: ACU
 - SoC: ST STR91x
 - Core: ARM966E-S [HTML](https://developer.arm.com/documentation/ddi0164/a) [PDF](https://documentation-service.arm.com/static/5e8e2e9dfd977155116a76a1) [archive.org link](https://web.archive.org/web/20240807035216/https://documentation-service.arm.com/static/5e8e2e9dfd977155116a76a1) (ARMv5TExP)
 - Firmware (ISO) URL: Same as EV-1 link (bundle).
 - Firmware PKG filename: `ACU_ReleaseV3_13.pkg`
 - Firmware PKG SHA-256: `5b60e177686731d1dd2ba4d9e8d8de1edc765d6b32110d1c765fcd768753ef7c`
 - Firmware version: 3.13
 - Firmware build date: 2022-06-27
 - Firmware OS: ThreadX

### ACU-??? Evolution autopilot Actuator Control Unit
 - SKU: ???-A
 - General component name: ACU (-A suffix, F2 revision?)
 - SoC: [STM32F4](https://www.st.com/en/microcontrollers-microprocessors/stm32f4-series.html)
 - Core: Cortex-M4 [HTML](https://developer.arm.com/documentation/100166/0001/) [PDF](https://documentation-service.arm.com/static/5fce431be167456a35b36ade) [archive.org link](https://web.archive.org/web/20230430053918/https://documentation-service.arm.com/static/5fce431be167456a35b36ade) (ARMv7E-M)
 - Firmware (ISO) URL: Same as EV-1 link (bundle).
 - Firmware PKG filename: `ACU_F2_Release_v3_15.pkg`
 - Firmware PKG SHA-256: `739dd79c0dc4e2ebfa160bb815a486171961c14d5112c02f0f14887936c97f0b`
 - Firmware version: 3.15
 - Firmware build date: 2023-09-11
 - Firmware OS: FreeRTOS

### p70r
 - SKU: E22167
 - General component name: P70
 - SoC: [Freescale (NXP) i.MX257](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-mature-processors/multimedia-applications-processors-data-acquisition-user-interaction-connectivity-arm9-core:i.MX257)
 - SoC docs: [Datasheet](https://www.nxp.com/docs/en/data-sheet/IMX25CEC.pdf) [archive.org link](https://web.archive.org/web/20240627061159/https://www.nxp.com/docs/en/data-sheet/IMX25CEC.pdf) [Reference Manual](https://www.nxp.com/docs/en/reference-manual/IMX25RM.pdf) [archive.org link](https://web.archive.org/web/20221206161500/https://www.nxp.com/docs/en/reference-manual/IMX25RM.pdf)
 - Core:
 - Firmware (ISO) URL: Same as EV-1 link.
 - Firmware (PKG from A Series Classic MFD) URL: [`https://flir.box.com/public/static/nh7s6r202umagcsi8vrj7jlu25nybxpm.zip`](https://flir.box.com/public/static/nh7s6r202umagcsi8vrj7jlu25nybxpm.zip) -> [`https://flir.app.box.com/public/static/nh7s6r202umagcsi8vrj7jlu25nybxpm.zip`](https://flir.app.box.com/public/static/nh7s6r202umagcsi8vrj7jlu25nybxpm.zip) -> [`https://public.boxcloud.com/d/1/<barf-removed>/download`](https://public.boxcloud.com/d/1/b1!coaGvRhBH2YU8SEIxMm-lOBHREDzFjhWV8dRVsc_WxKOUYCPxyV2h_JMhB0GSLJL6442sFVViDE8WHl2aYK-T965U1ha_K16EcBVv0ja57ySAFQ5LcpiC-af6Az0BrkxQHn-wv1JU6td66gIJ1YKvwTqIReaWJdsK2dTXsysJqaVfiDjyFYtfzw0TM9yJNVMQ2eMJ2Gf4cpkDNCm2S1sEQWvr6olTlcGxvaY-bXUVauq-XYDWizPKkWpm0v_UkVM3odxjmyqvh-Kh95OmJWEnGKb-RH8SgKU5KHsfccIa1mrciu1ciiXGI7aXp0pDukjYv5a1c2BWxJkbh7t1x-Gwxco5wXa9zUHbRFy3EAaxMSUgPiFfRVjmnyWAgnaXpjUNmutPomSPZ9f9sW3fB95ILQ2FYOc88rsz4jMqY9P4DvOigXjoYVmSzqko7_D6f8hAWrDj14mvbNshWF5K7Lg6JiIs3Sr2_Nj715EMTn9PINwf33kK16YoTWQjYhFFEtqF8Lzvdq66MyNdPrsALZWmCIJsqrQJdSwMTu9k5TcZT-Y-2wPmzYO2rJ_RMyTetDCgH0APEkbzPmsw7_9tAfaGlmfsaau4PQevkFmWFwkBNBE6i_szs5zTNYwYiqnlJglyBfWNIL35gpYTPXJG7kLQD6A7SspQjt48_t7dQYUtXteIUiLf1cYI_aLhsOOMs8_BLqWPU892yueTM8ptG9n78P4zyZV7cb4V834Uh0ZRVy93JxuIJdKXn1XY_RdsBYWEJkbxwDB1r9IylpFLzvcoX6C-O1hwdNMQrXwHcfli78n96f4CK6MgfFmSY5Qli2b-e1z31QHVQ9mHmrLBHJmxsaknZSANxQdKHLUNBrL9woCAefIcvOJvPRF6tiCeCh1jUEJlK6MwXxpYpeDuFUhbrKeupK1TzFzSpJxm_n-EzPxZ6S4EI18KNOS_ayllOUhWlNUahtIHC1TaaksGKadCJULckzKLs8-ZOkC_sbtu0QQA54lkqzlLRkPvZ7xEMVMZ6dCIIG3IBYfzVN_XezDGEqDYGE862IPuvyycFhXxNLnljnUpHRnsftC-IwiGg6zomqTj8-wgUEMLoF-OBNCHox0wXM62cy3uXbHGfpc-HYvZfwZBt4Xn-EfyX2hExIBtgVdmM-g85pwl2qmEtJkCRybRdvf2LOPM2MLnf6bP8Y5u3DX-uI0mzQ-Ma-2jiWRpTsqXPrRYYE-6x8nV7-kCwvTsXHJwFKZTqfjxN9taLByvsSxJQ-m7oKgwDwYaTx3Pv0FvIlfLsiFnJsfQg-JmCvFG3lGPGoW3pzRkpLJoFnHeo5VpNAJ537RCpI9hhQ_eD0wyo8B5ZqVG8tnUu9tvhFDmobxjCowXj-V0ZajusknvZVIqM11IMbUIZ4egHZ9/download) [archive.org link](https://web.archive.org/web/20240807023209/https%3A%2F%2Fpublic.boxcloud.com%2Fd%2F1%2Fb1!coaGvRhBH2YU8SEIxMm-lOBHREDzFjhWV8dRVsc_WxKOUYCPxyV2h_JMhB0GSLJL6442sFVViDE8WHl2aYK-T965U1ha_K16EcBVv0ja57ySAFQ5LcpiC-af6Az0BrkxQHn-wv1JU6td66gIJ1YKvwTqIReaWJdsK2dTXsysJqaVfiDjyFYtfzw0TM9yJNVMQ2eMJ2Gf4cpkDNCm2S1sEQWvr6olTlcGxvaY-bXUVauq-XYDWizPKkWpm0v_UkVM3odxjmyqvh-Kh95OmJWEnGKb-RH8SgKU5KHsfccIa1mrciu1ciiXGI7aXp0pDukjYv5a1c2BWxJkbh7t1x-Gwxco5wXa9zUHbRFy3EAaxMSUgPiFfRVjmnyWAgnaXpjUNmutPomSPZ9f9sW3fB95ILQ2FYOc88rsz4jMqY9P4DvOigXjoYVmSzqko7_D6f8hAWrDj14mvbNshWF5K7Lg6JiIs3Sr2_Nj715EMTn9PINwf33kK16YoTWQjYhFFEtqF8Lzvdq66MyNdPrsALZWmCIJsqrQJdSwMTu9k5TcZT-Y-2wPmzYO2rJ_RMyTetDCgH0APEkbzPmsw7_9tAfaGlmfsaau4PQevkFmWFwkBNBE6i_szs5zTNYwYiqnlJglyBfWNIL35gpYTPXJG7kLQD6A7SspQjt48_t7dQYUtXteIUiLf1cYI_aLhsOOMs8_BLqWPU892yueTM8ptG9n78P4zyZV7cb4V834Uh0ZRVy93JxuIJdKXn1XY_RdsBYWEJkbxwDB1r9IylpFLzvcoX6C-O1hwdNMQrXwHcfli78n96f4CK6MgfFmSY5Qli2b-e1z31QHVQ9mHmrLBHJmxsaknZSANxQdKHLUNBrL9woCAefIcvOJvPRF6tiCeCh1jUEJlK6MwXxpYpeDuFUhbrKeupK1TzFzSpJxm_n-EzPxZ6S4EI18KNOS_ayllOUhWlNUahtIHC1TaaksGKadCJULckzKLs8-ZOkC_sbtu0QQA54lkqzlLRkPvZ7xEMVMZ6dCIIG3IBYfzVN_XezDGEqDYGE862IPuvyycFhXxNLnljnUpHRnsftC-IwiGg6zomqTj8-wgUEMLoF-OBNCHox0wXM62cy3uXbHGfpc-HYvZfwZBt4Xn-EfyX2hExIBtgVdmM-g85pwl2qmEtJkCRybRdvf2LOPM2MLnf6bP8Y5u3DX-uI0mzQ-Ma-2jiWRpTsqXPrRYYE-6x8nV7-kCwvTsXHJwFKZTqfjxN9taLByvsSxJQ-m7oKgwDwYaTx3Pv0FvIlfLsiFnJsfQg-JmCvFG3lGPGoW3pzRkpLJoFnHeo5VpNAJ537RCpI9hhQ_eD0wyo8B5ZqVG8tnUu9tvhFDmobxjCowXj-V0ZajusknvZVIqM11IMbUIZ4egHZ9%2Fdownload)
 - Firmware (ZIP from A Series Classic) filename: `p70_(via_ASeries).zip`
 - Firmware (ZIP from A Series Classic) SHA-256: `a6065a3c4c70fe29891d9fb06ed9594276b65487116d298c8afac09e58f6d651`
 - Firmware PKG filename: `P70_313Pilot.pkg`
 - Firmware PKG SHA-256: `2d5e1de97b0b3c0128380283350e1f602f733a2a2905f801ea191393bfea3d5a`
 - Firmware PKG memory image name: `P70_RELEASE.mem`
 - Firmware PKG memory image size: 19,095,764 bytes
 - Firmware PKG memory image SHA-256: `d47f7065082188bc259c6b402c91873db8c259492215f7cecb1fa10ab806484c`
 - Firmware OS: ThreadX ARM9/Green Hills Version G4.0.4.0
 - Firmware version: 3.13
 - Firmware build date: ???
 - Bootloader (ISO) URL: [`https://raymarine.box.com/public/static/hscxoosrbq8sfeqwhobg6zi7qwpest26.iso`](https://raymarine.box.com/public/static/hscxoosrbq8sfeqwhobg6zi7qwpest26.iso) -> [`https://raymarine.app.box.com/public/static/hscxoosrbq8sfeqwhobg6zi7qwpest26.iso`](https://raymarine.app.box.com/public/static/hscxoosrbq8sfeqwhobg6zi7qwpest26.iso) -> [`https://public.boxcloud.com/d/1/b1!<barf-removed>../download`](https://public.boxcloud.com/d/1/b1!lRLja0pWcM9BQYl2X5I5QAmVntVGYTejDZpKIxiugQucPTnfHnNTaHlZSXQPYdCrPhOYHk4A92uWlOEqN8TmJrl3OgxfM-SqRLtf4C3HauY-hHxTN8aj9hH_28aaaYbJfu4QPK6Vo1K8sFLGRtwGyrlPtQ3Y1d6Nv6bxgbFo9upiQG5CxN4VBb438AIvyxaCmWcz0C89vvVD1TCEPoD1ryFykY8ZnXZGN2SGcI1ifvroqyhaiY2ePlzMqRaGTF_YXGSbmKRankYhd0o8bJdWGoPm4wZRg4u_j2-e0IlxF5ZJjY_Wd8qfxmUmoE7A0mbxjWqVfUFFb4uzIuo4b89Z4-cR31VFK__CFjOjx4tl7dtBR6S1QFQYeN3q7Or0_7DR3ePHqIibyaony70a_ehfbAqrOJY24iU8wl7i_mxKVJzmYe1crHVGKqIA4Q1OLQ2lnz2tGOQGMev9QHRz-9LHXE3mi4K0lhqM_Z-h1DlyibR53HRO4OZyKYeGRgqwVoFE0k8R1mnYHIMhGFAwGcJLyDnLNEsWbXculPmaQ-bbuzty8k7OO4wesH4Kphh9DL_5vHOFQX3jP6p7IoVY-vD5Z082WfTfFO4Nv_sj39D5YKe_nfMYpHZlxivQyUMQIQvGKElcmtmczIDuY06U_7KHGoTv51FUEmGkaS5C-2UENR1Zm1qmcuv9qedUI1z6aJhLy9BWlhTTpsoKOeujNoh49U0_lRaldL9H6JLmCDI7xNuoKr5hVCGFB3uulqIdgrvpkCxfDw3tum7VbUxTQEo6ya0IL-HM8vBuWmIZbliIkGPbOirPMvit7Hqh0QTTlrMfyE_RMjyojvLwvyHD5OxdvaMydVdJzhA5rPWph6PGeJcDSAxvIWXvOsK4BJsof4ouBkGyXOQpeJHmF578OCnbKI6rPY_1xM5ib0G9noe3K80pa1c1YgYp9BvZ-yfa5hhURRstO-GCkxiJZ1ptnbzeG2Yph57oRGXF65n3ssBZ2aBBmjRRrZ-5t2HBCKCBlqQv-XD3AUBdfLdJPCv84yy-KvMqA2oNL974tmhylEuDv8mL21FbLrOLrH4iRHvkq08RsMucJRmwkpvmQwAv5BcBNn3yPWiy1cORIswfSs33fpa4yfLrH5ozVoDiJsZoHZEUBtYDlOIYjHAcNnYX8qyjQbTUCRaFgkxO1AQGRJiFQNjYzZQucZbaJyTOcJUHeKZRfRZoB-KTNVVkdHOHcvOJS-J5SiszBK5V50Pkj1OzOtuzRjpcxhbqR3d8xBtEfVVCaWmpwOzrPSgomZ79yrBl14NgDuH5XV8LojfvZ1WlcWQ2ZhBCEmJR1zpuxjsIKzpQtK584dAcHiGPG2z4ePLsJdGGIH6gb26rKJbdp8QKD6Ngifq0vsA8LrLNSts0XZJ4c94SSjaayGx5uJNd66wxmNk5H34ltxt0u1n2I293SFFnusK3wVvodd8p7hJJ7LvA9xSKc9x8ncB79A../download) (archive.org link)[https://web.archive.org/web/20240807022325/https%3A%2F%2Fpublic.boxcloud.com%2Fd%2F1%2Fb1!lRLja0pWcM9BQYl2X5I5QAmVntVGYTejDZpKIxiugQucPTnfHnNTaHlZSXQPYdCrPhOYHk4A92uWlOEqN8TmJrl3OgxfM-SqRLtf4C3HauY-hHxTN8aj9hH_28aaaYbJfu4QPK6Vo1K8sFLGRtwGyrlPtQ3Y1d6Nv6bxgbFo9upiQG5CxN4VBb438AIvyxaCmWcz0C89vvVD1TCEPoD1ryFykY8ZnXZGN2SGcI1ifvroqyhaiY2ePlzMqRaGTF_YXGSbmKRankYhd0o8bJdWGoPm4wZRg4u_j2-e0IlxF5ZJjY_Wd8qfxmUmoE7A0mbxjWqVfUFFb4uzIuo4b89Z4-cR31VFK__CFjOjx4tl7dtBR6S1QFQYeN3q7Or0_7DR3ePHqIibyaony70a_ehfbAqrOJY24iU8wl7i_mxKVJzmYe1crHVGKqIA4Q1OLQ2lnz2tGOQGMev9QHRz-9LHXE3mi4K0lhqM_Z-h1DlyibR53HRO4OZyKYeGRgqwVoFE0k8R1mnYHIMhGFAwGcJLyDnLNEsWbXculPmaQ-bbuzty8k7OO4wesH4Kphh9DL_5vHOFQX3jP6p7IoVY-vD5Z082WfTfFO4Nv_sj39D5YKe_nfMYpHZlxivQyUMQIQvGKElcmtmczIDuY06U_7KHGoTv51FUEmGkaS5C-2UENR1Zm1qmcuv9qedUI1z6aJhLy9BWlhTTpsoKOeujNoh49U0_lRaldL9H6JLmCDI7xNuoKr5hVCGFB3uulqIdgrvpkCxfDw3tum7VbUxTQEo6ya0IL-HM8vBuWmIZbliIkGPbOirPMvit7Hqh0QTTlrMfyE_RMjyojvLwvyHD5OxdvaMydVdJzhA5rPWph6PGeJcDSAxvIWXvOsK4BJsof4ouBkGyXOQpeJHmF578OCnbKI6rPY_1xM5ib0G9noe3K80pa1c1YgYp9BvZ-yfa5hhURRstO-GCkxiJZ1ptnbzeG2Yph57oRGXF65n3ssBZ2aBBmjRRrZ-5t2HBCKCBlqQv-XD3AUBdfLdJPCv84yy-KvMqA2oNL974tmhylEuDv8mL21FbLrOLrH4iRHvkq08RsMucJRmwkpvmQwAv5BcBNn3yPWiy1cORIswfSs33fpa4yfLrH5ozVoDiJsZoHZEUBtYDlOIYjHAcNnYX8qyjQbTUCRaFgkxO1AQGRJiFQNjYzZQucZbaJyTOcJUHeKZRfRZoB-KTNVVkdHOHcvOJS-J5SiszBK5V50Pkj1OzOtuzRjpcxhbqR3d8xBtEfVVCaWmpwOzrPSgomZ79yrBl14NgDuH5XV8LojfvZ1WlcWQ2ZhBCEmJR1zpuxjsIKzpQtK584dAcHiGPG2z4ePLsJdGGIH6gb26rKJbdp8QKD6Ngifq0vsA8LrLNSts0XZJ4c94SSjaayGx5uJNd66wxmNk5H34ltxt0u1n2I293SFFnusK3wVvodd8p7hJJ7LvA9xSKc9x8ncB79A..%2Fdownload]
 - Bootloader ISO filename: `ray_Instruments_bootcode-web.upgrade.iso`
 - Bootloader ISO SHA-256: `261de5bc9499ff5d26bbaba5f7ace1c495106e224ec42be9eb6567cd6e339908`
 - Bootloader ISO `manifest.xml` SHA-256: `69e03daa194f019fcee2eceec174fa7caef6eec9fc993770bc53aeb04d9a3050`
 - Bootloader PKG filename: `I70_Bootloader_1_01.pkg`
 - Bootloader PKG SHA-256: `2f3f6f27c976c07e5f240533eaea62c4ad7e2832f691dad135046ed315a4b69a`
 - Bootloader version: 1.01
 - Bootloader build date: 2011-12-08

### A57d MFD
 - General component name: A Series Classic MFD
 - SKU:
 - SoC: Fujitsu "Jade" MB86R01
 - SoC Docs: [Datasheet](https://www.digikey.com/htmldatasheets/production/640362/0/0/1/mb86r01.pdf)
 - Core: ARM926EJ-S [HTML](https://developer.arm.com/documentation/ddi0198/e) [PDF](https://documentation-service.arm.com/static/5e8e3d1088295d1e18d3a9b2) [archive.org link](https://web.archive.org/web/20240807033826/https://documentation-service.arm.com/static/5e8e3d1088295d1e18d3a9b2) (ARMv5TEJ)
- Firmware (ZIP of PKG) URL: [`https://raymarine.box.com/shared/static/laq3jqfsdi0lzokffeue0h3wffyfmhjy.zip`](https://raymarine.box.com/shared/static/laq3jqfsdi0lzokffeue0h3wffyfmhjy.zip) -> [`https://raymarine.app.box.com/public/static/laq3jqfsdi0lzokffeue0h3wffyfmhjy.zip`](https://raymarine.app.box.com/public/static/laq3jqfsdi0lzokffeue0h3wffyfmhjy.zip) -> [`https://public.boxcloud.com/d/1/<barf-removed>/download`](https://public.boxcloud.com/d/1/b1!3T2g39MXkR85TlG6R7xT7_b5F8MXd-svBhW58EIfNclFRW9p5W-rTVs3lMrj0SGRWjRco3SJqtEYwO2cJB29s-WGPT7UNcQEkA-HfDZUiQ7Z0SSkShBkZa4LBGSEqTWaqk_NKiQh_NglhKdtSEG6x3MJoAwd_hObmF0yJ23vssowYM8tWluJQY9N6zhOPDuPgb1F2ZutAQRS4SaA5dYUKnzLzyW_i-dUh-RDlD8xTBV1WxgIVGLtaf7b1OGo-Z1m2oh9Vs90AHZmSzD3TnfSuv4Pg1btnvwrjdRVhN2njm3nJinfK2K9n64-AOWgbF0ea4seUufufbbOKzc0o3tL_2s1UkqDrfEtyPBD8vkwRrvNgoMjyMYX4qHnBkErQEh--3pkYQBUgq9E1GlaCipkUAHIfdT4C9_8uDjZdvJmpmy-x0dckYM7I4De7lNQe0TNUHErjD7Obw1aryHoe2wtsJN07fK7V3SVIyw0h70KzD_cVwx7_pA86o4CyrynMN_O2-pKd7I5QEcrg-cg1N60nWviEOuNk4xOoZAYJLXVpMmvKA5DPzmGT57TPAxjrAguw_yB5gwMjHFitJrUNfL87KS8eWazhYuwwrHGbOd469GL06NGjTbqrzlnUOw6CHI6Yo692x1MLm7pyL_cQiVAPEwxt0nDO6Sefe5H-0l5CSNNYHCgRBDLjdFp-70LtrhLeh0jEScl1BuVUTnVFvxnb7i9yZ4yU1ZlpeKEKj42Y4KVkkM5MwxqsQALGNeiKS7-0lonsI5p6TxNmWtCkD1DexZlOGMrGbSMfDpnnxREoGQpZkTepIm_7ZFGLi_nxeCY8e0ODOejhcJgldU3s7-tR0JU8b2m8TXWvsUF53ZQbaunMnV6eEGONVk3nKkJYFE9da9WX8gVSTNzLuasJUo7RVsYGVwhsBlAzHK36xZBsbvfB_72gl9yDhnyFAZsQz2VTcho52jQ_JP4aYVyx5zjfyP_ytgc_zBvHI4C7cgUL4sMJcg3Ze5SaYw8ohbi0iffPfzcReiVcGEd3Qub5RKhzEtUwR-23KfwoF7jUapJza6vHK7_OaP77qq7YYFh4r1kbXBTV46kE9jj6FSqio9SizOuBueBtVbGWzIf6qFmeEMIBmER44N7tvr1V7SgUpC-1Z0l0ef9rwmRPiKbuSjx3mXkjka_hYrDkT4YDlOzG1Z9JxHQev25SVIDK8JEimBcVNzAod7nTD6O4khRS85BJyIB_6SBIcFivQ4nSydEKsiU1lslvuv-pOYmBCNEtC1oT_jWq2IvkNW7t3ew8t4OFJrszjYaPrY-mVLjYwq_nLQEhWBjhH3fNl8Y0gqsuuWfdbkv2qL7RUPY4x1b0oyxlCYN4udVHPex8csGWT78tUK-ST1700WuIhD-yJSx0DcYNz4lODSJ0b-PRjtIPUZ1ZzME_r6BWUQY_GA./download) [archive.org link](https://web.archive.org/web/20240807024919/https://public.boxcloud.com/d/1/b1!rdCzbH0eZTvxpJ04c4BCjcxp5K-ppxU1AoguU7C1levS8Ey_aLlIxqgrlRf7VBKCIo8-kuOAJnM0x9cS7lu5DyAor8t76shpOt8iGdDJ-tjf61lXtROy-iGTGViP5z1n3qwu_jGwBZBqSCO0YwdSTzlkt4dxppZqRj3Ck9ZLBp3IGeIs-sjcObYcBVhyuG2cZvuktlaSXxvnlRPIXtPq7vVYq3vMGPSGKuTOm98o2MqN4FFj8GoQjpTbg0Lvo33HRve71CaU9-5g7MWZ8XKbOPgGo46clYzIXNfv7u-xPOdsxxEwKgpOLdI4-jdfQc7Wpoa2eDEtWSo1SDENE8YoW75KwyrxCcFchzwKbjMKNdge5peumz_rvKeg41clBifwZBaYQPXyTWe5JOFCtbIKUVT7yrWdEqVUzF0f3DAF_ZqfbEa5ySvCNZ4ltx20UU8Qic-w4wQ62psfbaTZNXNyYqPzuV6VfPgnZwP-mOqcAcpRSSvM_ymspP6D8zacZWVD4mxm-KkSA2Cu_Ezp00qIelbC-18qxd6zrS2ZyzAaTaTxxbteECyS0mqQC2hncnnMykhqBIylsOsPA6Ag71mYw-3jqtXeCnvXxSrvVOyIhT86gI_ZbwNls3cgc4fLyU85UfoaJChRFzxxoOxHj_DS1lxedZtyji7ALWsNifID8IAHDSJZ8a3VEp_kfBfwmzcg0d6bHvvvghQG_mnyjQH_ZXf6MVuw6zQt0P8fkaml73VAAOk9LwSYP8PAbvvRvqZoMHxyr--_SneoB6rXxyXsnj8HSRQhsWOMjeztplZIDje4ZoFMtZX_Gi1TpfMF_tIfVsYsGKOgM7UhmGLZCHBPwla06jqcYZ5-zpFuytI78-qxMzTqr0o7hsP_PHBzNwkbcU4m_r08isjWLFx6n7w17ELrVT66e1HoYDKFP4Xblk7syiOpmE7NG1WzyfqKk4xXYk2UW2GPFOjIv3Msra0gDQr9sicwQ-m5awJZnpfxgFD1Fk4DyHNa8riA4CdKCgkW6nNMLjVY6eG2CnhhJXMmbEaDQLlfq673ecnjzZrVBh5oOgOQ4GpNlW5nZGZiWp7-ZCVTKNxju6MfUH1jUim4rfxNF2QE_1yrOmHSbdwFXbFpmBnHEdK7ExyB4StGcN9OhM2pKpqck52idN9Y5g86wInIRaqnW6ksQUoOpU8MjOKqy1oLqyq6DooOV5iZI1U9qKWo3dX9bh778foICezRte0n0aRY8OystZp7VbJdRtPlWrlA0l_qZRGsudh4nZapBGRMAH3uv2VWYfk1i-aOsCFLGHtprcWjwN-DGQt5vEw5E39fl-PRmiyX18nT-5Jfs3yUyG6dOP4K8pVJWHjD5cJb-TYBglHWG9TpnHzzPbEC8tINdu3Ce1HcMzbuWuVz9s4Kr5WCbJ1L860xCn5_g_SCyGx705BxCSSl/download)
 - Firmware (ZIP of PKG) filename: `A_Series_v124.zip`
 - Firmware version: 1.24
 - Firmware PKG filename: `A_App_Upg.pkg`
 - Firmware PKG SHA-256: `b794a14cba31fe93b6c48a0ba7995d4ded4f25ea23b3b921e59c64bedf910bda`
 - Firmware PKG memory image name: `app.bin`
 - Firmware `app.bin` size: 20,082,760 bytes
 - Firmware `app.bin` SHA-256: `201734b5a35520664f2e02030284a2e8a4670c6b4886c89ecfba4e452eaaf10b`
 - Firmware build date: 2012-09-20
 - Firmware OS: ThreadX ARM9/Green Hills Version G4.0.4.0
 - Autorun filename: `autoruna.dob`
 - Autorun size: 297,788 bytes
 - Autorun version: 1.21
 - Autorun build date: 2008-11-05
 - Autorun `autoruna.dob` SHA-256: `d6f34a0a9eac1e39b3c61f7035fc53caeb70a81f0b68d24fcb806461511ea1db`
 - Autorun `update.mem` size: 904,532 bytes
 - Autorun `update.mem` SHA-256: `432932a884ea697233af00ef944c9b61bb5092bd1e44cb48543a8ff50e566d3c`
 - Autorun `update.mem` OS: ThreadX ARM9/Green Hills Version G4.0.4.0

### Type 0.5 autopilot hydraulic pump for 12 volt systems
 - SKU: E12139
