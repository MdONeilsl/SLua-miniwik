```lua

-- Legacy LSL alias. Prefer `quaternion` in new code.
export type rotation = quaternion

-- LSL list interop.
export type LSLTypes = string | number | vector | uuid | quaternion
export type LSLReadableTypes = LSLTypes | boolean
export type list = {LSLReadableTypes}

-- Event registration and dispatch.
type LLMultiEventName = {}
type LLSingleEventName = {}
export type LLEventName = LLMultiEventName | LLSingleEventName
type LLEventHandler = (...any) -> ()
type LLMultiEventHandler = (events: {DetectedEvent}) -> ()

-- LLTimers callback signatures.
type LLTimerEveryCallback = (scheduled: number, interval: number) -> ()
type LLTimerOnceCallback = (scheduled: number) -> ()
type LLTimerCallback = LLTimerEveryCallback | LLTimerOnceCallback

-- os.date / os.time tables.
export type DateTypeArg = {
    year: number,
    month: number,
    day: number,
    hour: number?,
    min: number?,
    sec: number?,
    isdst: boolean?,
}

export type DateTypeResult = {
    year: number,
    month: number,
    day: number,
    hour: number?,
    min: number?,
    sec: number?,
    wday: number?,
    yday: number?,
    isdst: boolean?,
}

-- lljson encode/decode options.
export type LLJsonEncodeOptions = {
    tight: boolean?,
    skip_tojson: boolean?,
    allow_sparse: boolean?,
    replacer: ((key: any, value: any, parent: {}?) -> any)?,
}

type LLJsonDecodeReviverWithoutPath = (key: string | number, value: any, parent: {}?, ctx: {}) -> any

type LLJsonDecodeOptionsWithoutPath = {
    track_path: false?,
    reviver: LLJsonDecodeReviverWithoutPath?,
} | LLJsonDecodeReviverWithoutPath

type LLJsonDecodeOptionsWithPath = {
    track_path: true,
    reviver: (key: string | number, value: any, parent: {}?, ctx: {path: {string | number}}) -> any,
}

export type LLJsonDecodeOptions = LLJsonDecodeOptionsWithoutPath | LLJsonDecodeOptionsWithPath

-- ll.* parameter tables.
export type AttachedListFilterParams = {[string]: any}       -- ll.GetAttachedListFiltered
export type CameraParams = {[string]: any}                   -- ll.SetCameraParams
export type CharacterParams = {[string]: any}                -- ll.CreateCharacter
export type CharacterNavigateParams = {[string]: any}        -- ll.NavigateTo
export type CharacterPatrolPointsParams = {[string]: any}    -- ll.PatrolPoints
export type CharacterPursueParams = {[string]: any}          -- ll.Pursue
export type CharacterWanderWithinParams = {[string]: any}    -- ll.WanderWithin
export type GetClosestNavPointParams = {[string]: any}       -- ll.GetClosestNavPoint
export type GetStaticPathParams = {[string]: any}            -- ll.GetStaticPath
export type GiveAgentInventoryParams = {[string]: any}       -- ll.GiveAgentInventory
export type GltfOverrides = {[string]: any}                  -- ll.SetLinkGLTFOverrides
export type HttpRequestParams = {[string]: any}              -- ll.HTTPRequest
export type KeyframedMotionParams = {[string]: any}          -- ll.SetKeyframedMotion
export type ParcelSaleParams = {[string]: any}               -- ll.SetParcelForSale
export type ParticleParams = {[string]: any}                 -- ll.LinkParticleSystem
export type PrimMediaParams = {[string]: any}                -- ll.SetLinkMediaParams

```
