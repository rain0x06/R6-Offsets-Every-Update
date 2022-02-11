# R6-Offsets-Code-Every-Update

Noclip: base+ 0x05FDF820 ] 0x98 ] 0x10 ] 0x5D8

Namespace offsets:
{
	static constexpr auto game_manager = 0x71FBDD8;
	static constexpr auto camera_manager = 0x60F0398;
	static constexpr auto profile_manager = 0x7033EB0;
}

Entity List: (*(uint64_t*)(gamebase + 0x71FBDD8) - 0x5013A972F916FB7Ei64) ^ 0x280DDB3232666F21i64) - 0x5A;

Weapon Data (WeaponManager): auto WeaponData = *(uint64_t*)(weapon + 0x218) ^ 0x45343509493F63F8i64;

No Recoil: *reinterpret_cast<uint32_t*>(WeaponData + 0x19C) = 0x44B3333E; (Encryption: _rotl(value ^ 0xEBB98598, 0x1) + 0x6D402809)

_________________________________________________________________________________________________________________________________________________________________________________
Code will be posted below this line:

New Outlines: 
void outlines(const uint64_t& actor) {
		const uint64_t& outline_component = *(const uint64_t*)(actor + 0x1C8) ^ 0xD5C0B11588D67FD4ui64;
		if (!outline_component) {
			return;
		}
 
		if (*(const uint64_t*)(outline_component + 0xB0) == 0) {
			return;
		}
 
		if (*(const uint64_t*)(outline_component + 0xB0) != 0x20748000) {
			*(uint64_t*)(outline_component + 0xB0) = 0x20748000;
		}
	}

_________________________________________________________________________________________________________________________________________________________________________________
Team ID: 
uint32_t get_team_id(uint64_t replication)
{
	auto v13 = driver::read(replication + 0x728) - 88;
 
	if ((v13 ^ 0x8087EB2FEBB40640ui64) == 23)
		return 6;
 
	auto v7 = ((((v13 ^ 0x8087EB2FEBB40640ui64) - 23 + 0xB4) + 0x4DE0D74E) ^ 0x11A281F9) - 27;
	return driver::read<uint32_t>(v7);
}
_________________________________________________________________________________________________________________________________________________________________________________
Game Manager:
{
	return (driver::read(process_base + offsets::game_manager) - 0x5013A972F916FB7Ei64) ^ 0x280DDB3232666F21i64;
}
_________________________________________________________________________________________________________________________________________________________________________________
Local Player:
uint64_t get_local_player(uint64_t profile_manager)
{
	auto v7 = driver::read(profile_manager);
	return _rotl64((driver::read(v7 + 0x48) - 0x2D7DB14E189509D5i64) ^ 0x6D59970CA20D421Di64, 16);
}
 
uint64_t get_entity_pawn(uint64_t addr)
{
	return (_rotl64(driver::read(addr + 0x38), 40) ^ 0x52A261F3563389E0i64) - 108;
}
_________________________________________________________________________________________________________________________________________________________________________________
