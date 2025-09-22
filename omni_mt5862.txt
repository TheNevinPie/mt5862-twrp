$(call inherit-product, $(SRC_TARGET_DIR)/product/full_base.mk)

# Add this line if your device is 64-bit
# Otherwise, If you have 32-bit device, add the below line instead of above line
$(call inherit-product, $(SRC_TARGET_DIR)/product/core_minimal.mk

# Another common config inclusion
$(call inherit-product, $(SRC_TARGET_DIR)/product/embedded.mk)

# If you are building from OmniROM's minimal source, Inherit some common Omni stuff.
$(call inherit-product, vendor/omni/config/common.mk)

# Replace $$DEVICE$$ with your Device Name's Value.
# Replace $$BRAND$$ with your Brand's / Manufacturer's Value.
PRODUCT_COPY_FILES += device/MediaTek/mt5862/prebuilt/zImage:kernel
# Fles under $(LOCAL_PATH)/recovery/root/ gets automatically copied into recovery
# PRODUCT_COPY_FILES += $(LOCAL_PATH)/recovery/root/*:root/*

PRODUCT_DEVICE := mt5862
PRODUCT_NAME := omni_mt5862
PRODUCT_BRAND := MediaTek
PRODUCT_MODEL := mt5862
PRODUCT_MANUFACTURER := MediaTek

# Forcefully add mtp support (adb is already there)
PRODUCT_DEFAULT_PROPERTY_OVERRIDES += \
    persist.sys.usb.config=mtp

# Add fingerprint from Stock ROM build.prop
PRODUCT_BUILD_PROP_OVERRIDES += \
    # These lines are from my device. You MUST Replace yours.
    BUILD_FINGERPRINT="MediaTek/m7332_eu/m7332_eu:9/PPR2.180905.006.A1/builder06101951:userdebug/dev-keys" \
    PRIVATE_BUILD_DESC="mt5862-userdebug 9 PPR2.180905.006.A1 TVOS-04.16.031.01.12 dev-keys"